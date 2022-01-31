Present: *Martin, Alex, Ben, Cristina, Frederik, Haris, Konrad, Luigi, Stefan, Yannick, Ann-Kathrin, Ben, Daniel, Nik*

# Firmware and Setup Status and Activities #

### Mainz ###
Martin:
* found out why our hardware Pixel masking did not work
* will need firmware change, would go for something more "final" now
* preliminary idea here: [Mupix Configuration](Mupix Configuration)

Nik:
* Test set-up finally working
* Now has ADC working separate form NIOS
* Failsafe programming next
* Then clean-up of FEB slow control

Alex:
* Working on IP unification, in particular uniform FIFOs. Simulation works and improves timing. Something in PCIe interface still broken.
* Next: Reomve spurious clock syncs on A10 board
* How are registers set/reset on startup?

### Zürich ###

Cristina:
* checking the data lines with a generated idle signal from NIOS (mutrig config "ALL_OFF"). 
* saw and decoded comma words with the oscilloscope
* checking idle signal quality (eye diagrams / bit error rates) for different lengths of samtec cable and for microtwisted pair cable 

![eyediagrams.jpeg](https://bitbucket.org/repo/7zKBgbq/images/2637213142-eyediagrams.jpeg)

* Nice!
* Maybe solder probes to get rid of blue eyes. Is this before or fater the equailzer?

### Geneva ###

Yannick:
* MuTrig1 evaluation working well with Stratix IV board
* Occasional PCIe hickups. Is the PCIe interface in sync with the latest version in the MuPix8 DAQ repo? 

### Heidelberg Pixels ###

Luigi:
* New student will start to work on setup with FEB and probe card

### Heidelberg Tiles ###

### KIT ###

# Software Status #

### MIDAS ###

* Stefan fixed a bug (and cleaned up the dummy front-end from Marius) - the MIDAS ring buffer now alos allows wrting multiple events. Statistics etc. work.
* Switching to standard library queues leads to a performance hit.
* MFE vs. TMFE: Use the c-style frontends, as the C++ front-end only supports a limited feature set and the main developer may have some lag.
* Let Stefan know if there are MIDAS-related warnings.
* Mainz will soon start to dest distributed DAQ system. 

### Heidelberg telescope upgrade ###
* PHY Control Interface now working
* New Quartus version in Mainz? Currently support 18-21 - newer versions require fixes in the NIOS. 21 has a broken editor.

# Cosmic run checklist #

* Many points being worked at

### Before we go to PSI ###

* Can configure MuPix and MuTrig from MIDAS via FEB reliably and with a MIDAS UI. 
* FEB SlowControl interface works reliably
* Have diagnostics for all links, PLLs and clocks in place, including MIDAS UI
* Sorter works in HW with data generators and source (also for MuTrig)
* We have a clear understanding how to handle 1.25 GBit link aligment, 8b/10b errors, resync etc.
* We can do run starts and configs with the ODB on the backend (i.e. not the switch and not the farm)
* We have a list of things to achieve with priorities
* We have committments from the participating groups towards these things

### Early stuff for PSI ###

* Set-up network including dedicated gateway, do performance tests
* Clear and re-cable the fibre fanout rack
* Recuperate the 2-3 fibres from the area

### Bitbucket issues ###

Have a look. Close things that are solved. Add issues if you discover them. Work to tackle them...

[See here](https://bitbucket.org/mu3e/online/issues?status=new&status=open)

## Next week ##

Some review to be found...