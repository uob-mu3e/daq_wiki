Goal: Custom pages for link and PLL monitoring

## FEBs ##

For the FEB the mupix arrival time histograms can be read from here
```
 -----------------------------------------------------------------
---- mupix PLL lock monitor (0x1200-0x12FF)----------------------
-----------------------------------------------------------------

    constant MP_HIT_ARRIVAL_START_REGISTER_R    :  integer := 16#1200#;       -- DOC: start of PLL lock monitor block, 4 Words for each chip, histogram lower bits of mupix arrival timestamp | MP_FEB
```
could be that it did not make it into the dev branch by now

```
   constant MP_LVDS_STATUS_START_REGISTER_W    :  integer := 16#1100#;       -- DOC: start of lvds status register block, 1 Word for each lvds link from here on | MP_FEB
        subtype  MP_LVDS_STATUS_DISP_ERR_RANGE  is integer range 27 downto 0; -- DOC: Disparity error counter in each lvds status register | MP_FEB 
        constant MP_LVDS_STATUS_PLL_LOCKED_BIT  :  integer := 28;             -- DOC: PLL locked bit in each lvds status register | MP_FEB 
        subtype  MP_LVDS_STATUS_STATE_RANGE     is integer range 30 downto 29;-- DOC: status Bit in each lvds status register | MP_FEB 
        constant MP_LVDS_STATUS_READY_BIT       :  integer := 31;             -- DOC: if set: this mupix lvds link is locked and ready | MP_FEB
```

ignore MP_LVDS_STATUS_STATE_RANGE

for the Si chips it is 
```
constant SI_STATUS_REGISTER                 :   integer := 16#FC2B#;
```

Martin: but if the Si chip is not ready / configured chances are low i would say that this makes it over the optical link from the FEB

Nik: Good point, this should be readable via the backplane

## SW and Farm boards ##

* PLL Registers SWB/Farm:

1. CNT_PLL_156_REGISTER_R(31) = locked
2. CNT_PLL_156_REGISTER_R(30 downto 0) = not locked cnt
3. CNT_PLL_250_REGISTER_R(31) = locked
4. CNT_PLL_250_REGISTER_R(30 downto 0) = not locked cnt

* Registers for sticky link locked monitoring

```
--FEB--> [ RX/TX ]   |   [ RX/TX ] --> Farm 
--FEB--> [ RX/TX ]   |   [ RX/TX ] --> Farm
--FEB--> [ RX/TX ]   |   [ RX/TX ] --> Farm

Dynamic and depending on how much links we have on the SWB the links to the farm are in low or in high
LINK_LOCKED_LOW_REGISTER_R
LINK_LOCKED_HIGH_REGISTER_R
```

* Global time counter

```
    --! time counter for getting the current time one the SWB
    --! reset if one of the FEBs send back the runNr at start of run
    process(i_clk, i_reset_n)
    begin
    if ( i_reset_n /= '1' ) then
        o_time_counter <= (others => '0');
    elsif rising_edge(i_clk) then
        o_time_counter <= time_counter + '1';
        if ( work.util.reduced_or(runNr_ack) = '1' ) then
            o_time_counter <= (others => '0');
        end if;
    end if:
    end process;
```
GLOBAL_TS_LOW_REGISTER_R, GLOBAL_TS_HIGH_REGISTER_R

## Merging data flow ##
Function for reading out data flow counter (counters are in a10_counters.vhd/h):

```
uint32_t read_counters(mudaq::DmaMudaqDevice & mu, uint32_t write_value, uint8_t link, uint8_t detector, uint8_t type)
{
    // SWB_COUNTER_ADDR_RANGE 7 downto 0
    // SWB_LINK_RANGE 15 downto 8 Link addrs for link specific counters
    // SWB_DETECTOR_RANGE 17 dowto 16 detector for readout, 00->PIXEL US, 01->PIXEL DS, 10->SCIFI
    // SWB_COUNTER_TYPE 18 counter type 0=link, 1=datapath
    mu.write_register(SWB_COUNTER_REGISTER_W, write_value | (link << 8) | (detector << 16) | (type << 18));
    return mu.read_register_ro(SWB_COUNTER_REGISTER_R);
}
```

* SWB:

1. 5 Link Counters per FEB
```
--FEB-->  |  SWB_EVENT_CNT | SWB_SUB_HEADER_CNT -> [ Link FIFO ] -> Data Path
          |                                        |         |
          V                                        V         V
  SWB_SKIP_EVENT_CNT              SWB_LINK_FIFO_FULL_CNT   SWB_LINK_FIFO_ALMOST_FULL_CNT
```
2. 6 Data Path Counters per detector (Pixel US, Pixel DS, Scifi) in round robin mode
The DMA_HALFFUL_REGISTER_R is not in this 6 counters (just a normal register) since we have only one DMA. 
```
                      (Back-Pressure)            
                  SWB_STREAM_FIFO_FULL_CNT             SWB_EVENTS_TO_FARM_CNT   
      |--------------------------------------------------|        ^
      |                                                  |        |            (Back-Pressure)
      V                                                  |        |          DMA_HALFFUL_REGISTER_R
[ Link FIFO ] ->                                         |        |        |-----------------------|
[ Link FIFO ] ->  [ Stream Round-Robin Readout Mode ] -> [ FIFO ] -> Farm  v                       |
[ Link FIFO ] ->                                      -> [ Debug FIFO ] -> Debug Event Builder -> DMA
                                                                           |                 |
                                                                           |                 |
                                                                           V                 |
                                         SWB_BANK_BUILDER_IDLE_NOT_HEADER_CNT                |
                                           SWB_BANK_BUILDER_TAG_FIFO_FULL_CNT                V
                                                                        SWB_BANK_BUILDER_SKIP_EVENT_CNT
                                                                        SWB_BANK_BUILDER_EVENT_CNT
```
3. TODO: N Data Path Counters per detector (Pixel US, Pixel DS, Scifi) in time merger mode.