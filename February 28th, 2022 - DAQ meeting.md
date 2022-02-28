Present: *Alex, Ann-Kathrin, Haris, Martin, Stefan, Ben, Marius, Konrad, Frederik, Yannick, Nik*

# Firmware, Software and Setup Status and Activities #

### Mainz ###
* setup of distributed system, having problems with clock box firmware compilation
* Martin: new and hopefully final firmware concept for mupix config including pixel masking was implemented, ready for review & lab-test - reviewed in the second half of the meeting
* Marius: SW board rewrite, merging tree works with headers, keep 32 bits and feed subtrees to farm links, optimizing this needs rate simulation. Review next week
* Marius working on farm for the cosmic run
* Haris: Event count on GPU working, now started hit count. SW currently running on a 1080Ti. To be decided which HW goes to PSI
* Alex: Cleaning up firmware, will tag a release now.
* Alex investigating if the driver can be made transparent to firmware uploads on the FPGA boards.

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