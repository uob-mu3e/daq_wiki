Present: *Alex, Martin, Ann-Kathrin, Cristina, Daniel, Marius, Sebastian, Gavin, Frederik, Nik*

# Firmware and Setup Status and Activities #

### Mainz ###
* Setup from December beam running again in the lab
* working on the points in the bitbucket issue list
* Monitoring of link status from the common slow control in the works, will be transferred from FEBs to the A10
* Issues with NIOS crashes on FEB will be looked at by Alex
* Alex tried Quartus 20 and 21. NIOS software needed a fix, otherwise everything is compiling. Things are neither better or faster than with earlier versions.

### Zürich ###
No news

### Genava ###
Not present

### Heidelberg Pixels ###
Daniel working on communicating with the PHY on to telescope adapter card. 

### Heidelberg Tiles ###
Not present

### KIT ###
No plan yet

# Software Status #

Nik working on evaluating databases, MongoDB looks like a good match

# Cosmic run checklist #

Nothing to be ticked off yet, but work ongoing on many points here.

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

## Next week ##

Analyzer Review (mostly Architecture) - Marius