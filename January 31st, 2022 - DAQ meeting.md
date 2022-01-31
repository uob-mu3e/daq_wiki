Present:

# Firmware and Setup Status and Activities #

### Mainz ###
* found out why our hardware Pixel masking did not work
* will need firmware change, would go for something more "final" now
* preliminary idea here: [Mupix Configuration](Mupix Configuration)

### Zürich ###
* checking the data lines with a generated idle signal from NIOS (mutrig config "ALL_OFF"). 
* saw and decoded comma words with the oscilloscope
* checking signal quality (eye diagrams / bit error rates) for different lengths of samtec cable and for microtwisted pair cable 


![eyediagrams.jpeg](https://bitbucket.org/repo/7zKBgbq/images/2637213142-eyediagrams.jpeg)

### Genava ###

### Heidelberg Pixels ###

### Heidelberg Tiles ###

### KIT ###

# Software Status #

### Heidelberg telescope upgrade ###
* PHY Control Interface
* New Quartus version in Mainz?
* topic in the right domain?

# Cosmic run checklist #

### Before we go to PSI ###

* Can configure MuPix and MuTrig from MIDAS via FEB reliably and with a MIDAS UI. 
* FEB SlowControl interface works reliably
* Have diagnostics for all links, PLLs and clocks in place, including MIDAS UI
* Sorter works in HW with data generators and source (also for MuTrig)
* We have a clear understanding how to handle 1.25 GBit link aligment, 8b/10b errors, resync etc.
* We can do run starts and configs with the ODB on the backend (i.e. not the switch and not the farm)
* We have a list of things to achieve with priorities
* We have committments from the participating groups towards these things

### Early suff for PSI ###

* Set-up network including dedicated gateway, do performance tests
* Clear and re-cable the fibre fanout rack
* Recuperate the 2-3 fibres from the area

### Bitbucket issues ###

[See here](https://bitbucket.org/mu3e/online/issues?status=new&status=open)

## Next week ##