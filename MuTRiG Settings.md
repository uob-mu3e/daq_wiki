#

| Name in JS GUI    | Description  | Comments  |
|-------------------|--------------|-----------|
| **DAQ Settings**  |              |           |
| DUMMY CONFIG      |If enabled, ignore different replies from ASICs when configuring via SPI|        |
| DUMMY DATA        |Enable dummy data generator on FPGA|           |
| DUMMY FAST        |Produce short events in dummy data generator on FPGA|           |
| DUMMY NUM         |Number of hits to be generated per ASIC using the FPGAs dummy data generator|    |
| PRBS decoder disable |Bypass PRBS decoder on the FPGA|           |
| Wait for all      |Data receivers are only allowed to produce frames when all enabled receivers are locked. Helps to keep synchronization and avoid buffer overruns at start of a run.|           |
| Wait for all sticky |Once a receiver has locked, do not stop producing data even if the link is lost. Ready bits are reset at start of run.|           |
| Reset Blocks      |              |           |
| **Global Settings** |            |           |
| Num Asics         |              |           |
| EXT TRG OFFSET    |configuration of external trigger|           |
| EXT TRG ENDT      |              |           |
| DEBUG             |              |           |
| PRBS_SINGLE       |only one PRBS event per frame|In the PRBS_DEBUG mode, if PRBS_SINGLE is selected, then there will be only 1 48-bit PRBS data in each data frame.|
| EXT TRG           |              |           |
| GEN IDLE          |enables comma word in LVDS data stream|           |
| DIS COARSE        |              |           |
| SHORT             |enables short event mode, only T-timestamps and
E-flags are transmitted|Other names: Fast mode, SciFi mode|
| PRBS              |Enables PRBS generation in MuTRiG digital part|The output data will be 48-bit PRBS data. If PRBS_SINGLE is not selected, there will be 255 PRBS data each frame.|
| SYNC_CH_RST       |Sync. PLL Reset|'1': Use internally synchronized (2FF-synchronizer) version of reset signal for PLL reset.      '0': Feed reset input to pll directly.|
| EXT TRG ENDT SIGN |              |           |
| PLL COARSE        |              |           |
| PLL ENVMON        |              |           |
| **PLL Settings**  |              |           |
| VNPFC             |              |           |
| VNCnt             |              | If you see spikes in the coarse counter distribution, increase this. Set 0 to "unlock" PLL. |
| VNVCOBuffer       |              |           |
| VNVD2C            |              |           |
| VNPCP             |              |           |
| VNHitLogic        |              | Used to tune PLL locking at wrong frequencies. Increase if you see "side peaks". |
| VNCntBuffer       |              |           |
| VNVCODelay        |              | Used to tune PLL locking at wrong frequencies. |
| LATCHBIAS         |              |           |
| MS Limits         |              |           |
| MS Polarity       |              |           |
| ** Monitor Driver Settings** |   | **Not connected on SMB2** |
| AMON              |              |           |
| DMON 1            |Bias current and enable for Q/T digital monitor. Higher value=higher current.|           |
| DMON 2            |Bias current and enable for flag/E digital monitor. Higher value=higher current.|           |
| **LVDS Driver Settings** |       |           |
| LVDS VCM          |LVDS driver common mode voltage.| Typical value=155=1.1V (0 = 0V, 255=1.8V)    |
| LVDS BIAS         |The additional bias for LVDS TX.|The LVDS is already biased with 4.5mA tail current. This DAC is used in case the LVDS TX need higher driving power. 0=0A, 63=4.5A. Default value is 0.|
| **Channel Settings** |           |           |
| TTHRESH           |T-threshold setting.|From 0 to 63. Lower values are higher thresholds, zero (noise) is around 32. |
| TTHRESH Scale     |T-Threshold current scaling.| 0=1:1 4=1:2 (1:2 means higher maximum threshold). According to Simon's thesis, the dynamic range at 0 is maximized. |
| ETHRESH           |E-Threshold, see above. |0: 1.8V; 255: 0. The energy signal for discrimination has an offset. Changing the T-threshold will also change this offset. For SiPM signals, the value is usually between 90 - 150.|
| MASK              | Mask a channel (so you don't read it out) |For noisy channels|
| SIPM              |Voltage tuning at SiPM input terminal.|  0=low voltage, 63=high voltage. Keep at values in the middle (~15, up to twenty-something). Scaling: 0=normal, 1=higher current. This setting changes the voltage at the input of the terminal and effective changes the over-voltage of SiPM.|
| INPUTBIAS         |Main bias current of the input stage, affects all later stages (i.e. also thresholds, SiPM voltage) and general performance.|Higher values means higher current. Set to 2, up to 4. Tuning the bias current of the input stage. It changes the bandwidth, input impedance, input terminal voltage and also effects the timing and energy resolution. This DAC changes overall performance of the chip.|
| POLE              |DAC setting for pole-zero cancellation feature|Leave this off|
| EBIAS             |              |           |
| AMPCOM            |Tuning the bias current of amplifers, to change the gain of the amplifer and the hysteresis of the comparator.|scale = 0: value 0: no effect, value 63: high gain, less hysteresis;scale = 3: value 0: no effect, value 63: low gain, higher hysteresis. For now, set to 0, scale to 2 (turn off)|
| CML               | Current Mode Logic |Set to middle values (8), scale to 0. For TDC injection, set to 0. From Mutrig DAQ: *Tuning the CML logic driving strength, for the communication between analog front-end and TDC. This settting should match with TDC hitlogic setting.* |
| AMON CTRL         |Ananlog monitor selection|0: no selection; 1: top_monitor; 2: input stage cascode voltage; 3: Timing trigger monitor P; 4: SiPM_vbias, SiPM cascode bias; 5: Timing trigger monitor N; 6: fb_pbias<br />7: Energy trigger monitor N|
| COMP SPI          |Change the tail compensation effect.|1: moderate tail compensation; 2: aggressive tail compensation. Not so relevant to us.|
| TDCTEST_N         |Disable TDC test input to this channel|(0 enables TDC input and shorts with the normal hitlogic output. Note that DMON and tdc test signals are shared, so only one can be used at a time, this requires hardware changes - typically removing a jumper)|
| S SWITCH          |Single-ended or differetial signals| Set to 0 |
| DELAY             |           | Set to 0 |
| ENERGY_C_EN       |Enable the Capacitantor in the low pass filter before the E-Comparator.|           |
| ENERGY_R_EN       |Enable the Resistor in the low pass filter before the E-Comparator.|           |
| SENSING_HIGH_R    |Enables high impedance source in the feedback path. | Should be set to 0|
| EDGE              |Select polarity of E-branch comparator| See also EDGE CML |
| EDGE CML          |Invert polarity of digital signals to hitlogic in channel.|           |
| DMON ENA          |Enable digital monitor for this channel. |**Maximum one should be enabled at all times!** Leave off with SMB|
| DMON SW           |Digital monitor output mode. |0: Show Q and flag output (as it goes to the TDC), 1: show raw T & E flags|
| RECV ALL          | Send the hit structure of "long" events, but the *Energy timestamo* is actually the next T timestamp |  |
| POLE_EN_N         |0: enable dac for PZC.| Only controls the dac, not the feature itself|
| AMON_EN_N         |1: disable analog monitor output from this channel. |**Analog monitor should only be enabled for up to one channel in a chip!** Leave off with SMB |

Missing: Coincidence logic

Sources:
- [Simon's Thesis](https://www.psi.ch/sites/default/files/import/mu3e/ThesesEN/DissertationCorrodi.pdf),
- [Custom page tooltips](https://bitbucket.org/mu3e/online/src/master/mhttpd/custom/mutrigTdc.html),
- *KIP MuTRiG configGUI* tooltips from KIP


## Mapping Midas parameters names to Mutrig-daq parameters names ##

**Global Settings** 
ODB: /Equipment/SciFiCentral/Settings/ASICs/Global/

#

| Midas daq (ODB/custom page)                       | Mutrig-daq  |
|-------------------------------|----------|
| ext_trig_mode                 | EXT_TRIG_MODE |
| ext_trig_endtime_sign         | EXT_TRIG_SIGN_FORW_TIME |
| ext_trig_offset               | EXT_TRIG_BACK_TIME |
| ext_trig_endtime              | EXT_TRIG_FORW_TIME |
| gen_idle                      | O_GEN_IDLE_SIGNAL |
| ms_debug                      | MS_DEBUG |
| prbs_debug                    | PRBS_DEBUG |
| prbs_single                   | PRBS_SINGLE |
| sync_ch_rst                   | SYNC_CH_RST |
| disable_coarse                | DISABLE_COARSE |
| pll_setcoarse                 | PLL1_SETCOARSE |
| short_event_mode              | FAST_TRANS_MODE |
| pll_envomonitor               | PLL1_ENVCOMONITOR |
| pll_lol_dbg                   | PLL_LOL_dbg |
| en_ch_evt_cnt                 | EN_CH_EVT_CNT |

** Chip settings ** 
ODB: /Equipment/SciFiCentral/Settings/ASICs/TDCs/

| Midas daq (ODB/custom page)                       | Mutrig-daq  |
|------------------------------|----------|
| vnpfc                        | DAC_TDC_VNPFC |
| vnpfc_offset                 | DAC_TDC_VNPFC_OFFSET |
| vnpfc_scale                  | DAC_TDC_VNPFC_SCALE |
| vncnt                        | DAC_TDC_VNCnt |
| vncnt_offset                 | DAC_TDC_VNCnt_OFFSET |
| vncnt_scale                  | DAC_TDC_VNCnt_SCALE |
| vnvcobuffer                  | DAC_TDC_VNVCOBUFFER |
| vnvcobuffer_offset           | DAC_TDC_VNVCOBUFFER_OFFSET |
| vnvcobuffer_scale            | DAC_TDC_VNVCOBUFFER_SCALE |
| vnd2c                        | DAC_TDC_VND2C |
| vnd2c_offset                 | DAC_TDC_VND2C_OFFSET |
| vnd2c_scale                  | DAC_TDC_VND2C_SCALE |
| vnpcp                        | DAC_TDC_VNPCP |
| vnpcp_offset                 | DAC_TDC_VNPCP_OFFSET |
| vnpcp_scale                  | DAC_TDC_VNPCP_SCALE |
| vnhitlogic                   | DAC_TDC_VNHITLOGIC |
| vnhitlogic_offset            | DAC_TDC_VNHITLOGIC_OFFSET |
| vnhitlogic_scale             | DAC_TDC_VNHITLOGIC_SCALE |
| vncntbuffer                  | DAC_TDC_VNCntBuffer |
| vncntbuffer_offset           | DAC_TDC_VNCntBuffer_OFFSET |
| vncntbuffer_scale            | DAC_TDC_VNCntBuffer_SCALE |
| vnvcodelay                   | DAC_TDC_VNVCODELAY |
| vnvcodelay_offset            | DAC_TDC_VNVCODELAY_OFFSET |
| vnvcodelay_scale             | DAC_TDC_VNVCODELAY_SCALE |
| latchbias                    | DAC_TDC_LATCHBIAS |
| ms_limits                    | MS_LIMITS |
| ms_switch_sel                | MS_SWITCH_SEL |
| amon_en_n                    | AMON_EN |
| amon_dac                     | AMON_DAC |
| ??                           | COIN_WND |
| dmon_1_en                    | DIG_MON1_EN |
| dmon_1_dac                   | DIG_MON1_DAC |
| dmon_2_en                    | DIG_MON2_EN |
| dmon_2_dac                   | DIG_MON2_DAC |
| lvds_tx_vcm                  | LVDS_TX_VCM |
| lvds_tx_bias                 | LVDS_TX_BIAS |
| coin_xbar_lower_rx_ena       | COIN_XBAR_lower_RX_ena |
| coin_xbar_lower_tx_ena       | COIN_XBAR_lower_TX_ena |
| coin_xbar_lower_tx_vdac      | COIN_XBAR_lower_TX_vDAC |
| coin_xbar_lower_tx_idac      | COIN_XBAR_lower_TX_iDAC |
| coin_mat_xbl                 | COIN_MAT_XBL |
| coin_mat_xbu                 | COIN_MAT_XBH |
| coin_xbar_upper_rx_ena       | COIN_XBAR_upper_RX_ena |
| coin_xbar_upper_tx_ena       | COIN_XBAR_upper_TX_ena |
| coin_xbar_upper_tx_vdac      | COIN_XBAR_upper_TX_vDAC |
| coin_xbar_upper_tx_idac      | COIN_XBAR_upper_TX_iDAC |

** Channel settings **
OBD: /Equipment/SciFiCentral/Settings/ASICs/Channels/

| Midas daq (ODB/custom page)                       | Mutrig-daq  |
|-------------------------------|----------|
| mask                          | DAC_CHANNEL_MASK_CH |
| recv_all                      | RECV_ALL_CH |
| tthresh                       | DAC_TTHRESH_CH |
| tthresh_sc                    | DAC_TTHRESH_SC_CH |
| ethresh                       | DAC_ETHRESH_CH |
| ebias                         | DAC_EBIAS_CH |
| sipm                          | DAC_SIPM_CH |
| sipm_sc                       | DAC_SIPM_SC_CH |
| inputbias                     | DAC_INPUTBIAS_CH |
| inputbias_sc                  | DAC_INPUTBIAS_SC_CH |
| pole                          | DAC_POLE_CH |
| pole_sc                       | DAC_POLE_SC_CH |
| ampcom                        | DAC_AMPCOM_CH |
| ampcom_sc                     | DAC_AMPCOM_SC_CH |
| cml                           | DAC_CML_CH |
| cml_sc                        | DAC_CMLSCALE_CH |
| amonctrl                      | AMON_CTRL_CH |
| comp_spi                      | COMP_SPI_CH |
| coin_mat                      | COIN_MAT_CH |
| tdctest_n                     | TDCTEST_CH |
| sswitch                       | S_SWITCH_CH |
| delay                         | DAC_DELAY_CH |
| pole_en_N                     | DAC_DELAY_BIT1_CH |
| energy_c_en                   | ANODE_FLAG_CH |
| energy_r_en                   | CATHODE_FLAG_CH |
| cm_sensing_high_r             | SORD_CH |
| amon_en_n                     | SORD_NOT_CH |
| edge                          | EDGE_CH |
| edge_cml                      | EDGE_CML_CH |
| dmon_en                       | DMON_ENA_CH |
| dmon_sw                       | DMON_SW_CH |