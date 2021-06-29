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

Sources: [Simon's Thesis](https://www.psi.ch/sites/default/files/import/mu3e/ThesesEN/DissertationCorrodi.pdf), [Custom page tooltips](https://bitbucket.org/mu3e/online/src/master/mhttpd/custom/mutrigTdc.html), *KIP MuTRiG configGUI* tooltips from KIP