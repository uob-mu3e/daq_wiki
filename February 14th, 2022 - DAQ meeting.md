Present:

# Firmware, Software and Setup Status and Activities #

### Mainz ###

Nik:

* Failsafe programming working
* FEB crate control FE reworked and tested
* Working on slow control/link management refactoring, see [Addressing and managingFEBs](Addressing and managingFEBs)

### Zürich ###

Cristina (on sick leave):

* Compared CLK transmission (625 MHz) with samtec and microtwisted pairs:
![CLK.png](https://bitbucket.org/repo/7zKBgbq/images/4193245209-CLK.png)

* Checked data line before equalizer (at DAB test point), after equalizer (at DAB-FEB connector) and after equalizer and pre-emphasis (at DAB-FEB connector). Findings:
(1) Equalizer behaves as expected but introduces jitter. How much jitter can the FEB tolerate?
(2) Pre-emphasis distorts the signal and won't be used in DAB, but perhaps in the SMB.
![Screen Shot 2022-02-13 at 19.14.56.png](https://bitbucket.org/repo/7zKBgbq/images/361622784-Screen%20Shot%202022-02-13%20at%2019.14.56.png)

* Currently trying to check data lines with PRBS data, but don't manage to see anything different to K28.5 with the PRBS single configuration (investigating). 

* Proposal for SciFi DAQ meeting next week (Cristina, Yannick, Konrad, Marius, Martin, Nik ..?) to discuss milestones, roadmap and group contributions. Next Monday after DAQ meeting?

### Geneva ###


### Heidelberg Pixels ###


### Heidelberg Tiles ###

### KIT ###

### MIDAS ###

### Heidelberg telescope upgrade ###

* Arrived hardware:
    * PHY does not work
    * Remote test of the fourth card possible
* Currently working on the data path
* Is an OS running on the NIOS?

### Pull requests ###

What can we merge?

[See here](https://bitbucket.org/mu3e/online/pull-requests/)

### Bitbucket issues ###

Have a look - the list is not getting shorter (yet?). Close things that are solved. Add issues if you discover them. Work to tackle them...

[See here](https://bitbucket.org/mu3e/online/issues?status=new&status=open)


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

### Early stuff for PSI ###

* Set-up network including dedicated gateway, do performance tests
* Clear and re-cable the fibre fanout rack
* Recuperate the 2-3 fibres from the area



## Next week ##

Some review to be found...