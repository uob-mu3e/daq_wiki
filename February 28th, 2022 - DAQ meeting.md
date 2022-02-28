Present: 

# Firmware, Software and Setup Status and Activities #

### Mainz ###
* setup of distributed system, having problems with clock box firmware compilation
* new and hopefully final firmware concept for mupix config including pixel masking was implemented, ready for review & lab-test

### Zürich ###


### Geneva ###


### Heidelberg Pixels ###


### Heidelberg Tiles ###


### KIT ###


### MIDAS ###


### Heidelberg telescope upgrade ###


### Pull requests ###

What can we merge?

[See here](https://bitbucket.org/mu3e/online/pull-requests/)

### Bitbucket issues ###

Have a look - the list is not getting shorter (yet?). Close things that are solved. Add issues if you discover them. Work to tackle them... Use CRITCAL for issues that are needed for the cosmic run.

[See here](https://bitbucket.org/mu3e/online/issues?status=new&status=open)


# Cosmic run checklist #


### Before we go to PSI ###

* Can configure MuPix and MuTrig from MIDAS via FEB reliably and with a MIDAS UI. 
* FEB SlowControl interface works reliably
* Have diagnostics for all links, PLLs and clocks in place, including MIDAS UI
* Sorter works in HW with data generators and source (also for MuTrig)
* We have a clear understanding how to handle 1.25 GBit link aligment, 8b/10b errors, resync etc.
* We can do run starts and configs with the ODB on the backend (i.e. not the switch and not the farm)
* We have a list of things to achieve with priorities

### Early stuff for PSI ###

* Set-up network including dedicated gateway, do performance tests
* Clear and re-cable the fibre fanout rack
* Recuperate the 2-3 fibres from the area

## Review of MuPix config ##
Overview:
https://bitbucket.org/mu3e/online/wiki/Mupix%20Configuration

code:
https://bitbucket.org/mu3e/online/src/martin_dev/fe_board/fe_mupix/mupix_block/slowcontrol/

"mupix_ctrl.vhd" and below

## Next week ##