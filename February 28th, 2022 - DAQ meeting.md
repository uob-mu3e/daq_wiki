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

SciFi Hackathlon ongoing
* DAB pinout maybe incorrect (later in the day: equalizers were shut off).
* Config can be read back to NIOS
* DABs are nicely probable, which helps a lot - design future DABs also for probability
* Plan is to see MuTrig data, play with config to get PLL locked
* Six SciFi boards with MuTrigs at hand, try to identify good ones for cosmic run
* Priority is to get meaningful data, sorting is only a strecth goal.

### Geneva ###

* In Zürich for the Hackatlon

### Heidelberg Pixels ###

* Twisting micro-cables

### Heidelberg Tiles ###

* MuTrig 3 requirements doucment in circulation, Konrad will turn comments into requirements.
* Two invalid 8b/10b words during reset not seen as a problem

### KIT ###

* Will put together test system, to be discussed with Nik this week

### MIDAS ###

* Stefan fiexed several issues
* Some ideas to fix warnings, Nik will check
* Restarting runs is broken in MEG, maybe related to what Marius sees in the dummy Farm FE, Stefan working on it

### Setup at PSI ###

* Mainz will bring a few PCs for control room if they arrive in time
* Mainz might start setup during the Wengen week, Stefan is at PSI until the 17th
* 10 Crate controllers ready, one chip missing. Nik tries via non-official suppliers
* 8 optical fibre to MIDAS boxes in crate with power supply available. Will need eight ethernet slots - swithc should be sufficient

### Heidelberg telescope upgrade ###


### Pull requests ###

What can we merge? 

* Alex will merge one (optional CUDA), then tag.

[See here](https://bitbucket.org/mu3e/online/pull-requests/)

### Bitbucket issues ###

Have a look - the list is not getting shorter (yet?). Close things that are solved. Add issues if you discover them. Work to tackle them... Use CRITCAL for issues that are needed for the cosmic run.

[See here](https://bitbucket.org/mu3e/online/issues?status=new&status=open)


# Cosmic run checklist #

Hard at work on all of them, nothing done yet.

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

Regular DAQ meeting plus review of the switching firmware, maybe also A10 block. Farm to follow.