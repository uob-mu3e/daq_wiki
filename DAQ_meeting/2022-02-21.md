# DAQ meeting 2022-02-21

Present: *...*



## Firmware, Software and Setup Status and Activities #

### Mainz ###

- Alex: remove pcie1, remove 156 -> 250 transition, only use 250

- Marius:
    - where do we put ddr ram to (a10_block, etc.)
    - add fifo to transition from pcie to ddr
    - compiled ddr4

### Zürich ###

no news

- Cristina:
    - talk about plans at the end of meeting within group

### Geneva ###

no news

### Heidelberg Pixels ###

- Luigi: still working on testbeam
    - improve configuration

### Heidelberg Tiles ###

### KIT ###

no news

### MIDAS ###

### Heidelberg telescope upgrade ###

- Daniel:
    - test adapter card, 2 working with working phi,
      2 with nonworking phi chips, working on ethernet conn data path

## Bitbucket

### Pull Requests ###

[See here](https://bitbucket.org/mu3e/online/pull-requests/)

### Issues ###

[See here](https://bitbucket.org/mu3e/online/issues?status=new&status=open)



## Cosmic run checklist #

* Many points being worked at, nothing can be ticked off yet.

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



## Next week ##

