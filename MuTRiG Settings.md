| Name in JS GUI    | Description  | Comments  |
|-------------------|--------------|-----------|
| **DAQ Settings**  |              |           |
| DUMMY CONFIG      |If enabled, ignore different replies from ASICs when configuring via SPI|        |
| DUMMY DATA        |Enable dummy data generator on FPGA|           |
| DUMMY FAST        |Produce short events in dummy data generator on FPGA|           |
| DUMMY NUM         |Number of hits to be generated per ASIC using the FPGAs dummy data generator|    |
| PRBS decoder disable |Bypass PRBS decoder on the FPGA|           |
| Wait for all      |Data receivers are only allowed to produce frames when all enabled receivers are locked. Helps to keep synchronization and avoid buffer overruns at start of a run.|           |
| Wait for all sticky |Once a receiver has locked, do not stop producing data even if it the link is lost. Ready bits are reset at start of run.|           |
| Reset Blocks      |              |           |
| **Global Settings** |            |           |
| Num Asics         |              |           |
| EXT TRG OFFSET    |              |           |
| EXT TRG ENDT      |              |           |
| DEBUG             |              |           |
| PRBS_SINGLE       |              |           |
| EXT TRG           |              |           |
| GEN IDLE          |              |           |
| DIS COARSE        |              |           |
| SHORT             |              |           |
| PRBS              |              |           |
| SYNC_CH_RST       |              |           |
| EXT TRG ENDT SIGN |              |           |
| PLL COARSE        |              |           |
| PLL ENVMON        |              |           |
| **PLL Settings**  |              |           |
| VNPFC             |              |           |
| VNCnt             |              |           |
| VNVCOBuffer       |              |           |
| VNVD2C            |              |           |
| VNPCP             |              |           |
| VNHitLogic        |              |           |
| VNCntBuffer       |              |           |
| VNVCODelay        |              |           |
| LATCHBIAS         |              |           |
| MS Limits         |              |           |
| MS Polarity       |              |           |
| ** Monitor Driver Settings** |   | **Not connected on SMB2** |
| AMON              |              |           |
| DMON 1            |Bias current and enable for Q/T digital monitor. Higher value=higher current.|           |
| DMON 2            |Bias current and enable for flag/E digital monitor. Higher value=higher current.|           |
| **LVDS Driver Settings** |       |           |
| LVDS VCM          |LVDS driver common mode voltage.| Typical value=155    |
| LVDS BIAS         |LVDS driver bias current. Higher value is higher current.|           |
| **Channel Settings** |           |           |
| TTHRESH           |T-threshold setting.|From 0 to 63. Lower values are higher thresholds, zero (noise) is around 32. |
| TTHRESH Scale     |T-Threshold current scaling.| 0=1:1 4=1:2 (1:2 means higher maximum threshold)|
| ETHRESH           |E-Threshold, see above. |From 0 to 255|
| MASK              | Mask a channel (so you don't read it out) |For noisy channels|
| SIPM              |Voltage tuning at SiPM input terminal.|  0=low voltage, 63=high voltage. Keep at values in the middle. Scaling: 0=normal, 1=higher current|
| INPUTBIAS         |Main bias current of the input stage, affects all later stages (i.e. also thresholds, SiPM voltage) and general performance.|Higher values means higher current.|
| POLE              |DAC setting for pole-zero cancellation feature|           |
| EBIAS             |              |           |
| AMPCOM            |Tuning the bias current of amplifers, to change the gain of the amplifer and the hysteresis of the comparator.|scale = 0: value 0: no effect, value 63: high gain, less hysteresis;scale = 3: value 0: no effect, value 63: low gain, higher hysteresis.|
| CML               |              |           |
| AMON CTRL         |Ananlog monitor selection|0: no selection<br />1: top_monitor<br />2: input stage cascode voltage<br />3: Timing trigger monitor P<br />4: SiPM_vbias, SiPM cascode bias<br />5: Timing trigger monitor N<br />6: fb_pbias<br />7: Energy trigger monitor N|
| COMP SPI          |Change the tail compensation effect.|1: moderate tail compensation\n2: aggressive tail compensation|
| TDCTEST_N         |Disable TDC test input to this channel|(0 enables TDC input and shorts with the normal hitlogic output. Note that DMON and tdc test signals are shared, so only one can be used at a time, this requires hardware changes - typically removing a jumper)|
| S SWITCH          |Single-ended or differetial signals|           |
| DELAY             
| ENERGY_C_EN       |Enable the Capacitantor in the low pass filter before the E-Comparator.|           |
| ENERGY_R_EN       |Enable the Resistor in the low pass filter before the E-Comparator.|           |
| SENSING_HIGH_R    |Enables high impedance source in the feedback path. | Should be set to 0|
| EDGE              |Select polarity of E-branch comparator| See also EDGE CML |
| EDGE CML          |Invert polarity of digital signals to hitlogic in channel.|           |
| DMON ENA          |Enable digital monitor for this channel. |Maximum one should be enabled at all times! |
| DMON SW           |Digital monitor output mode. |0: Show Q and flag output (as it goes to the TDC), 1: show raw T & E flags|
| RECV ALL          |              |           |
| POLE_EN_N         |0: enable dac for PZC.| Only controls the dac, not the feature itself|
| AMON_EN_N         |1: disable analog monitor output from this channel. |**Analog monitor should only be enabled for up to one channel in a chip!**|


Missing: Coincidence logic