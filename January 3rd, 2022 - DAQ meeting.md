Present: *Konrad, Sophie, Marius, Haris, Yannick, Martin, Alex, Frederik, Nik*

# Goals for 2022 #

BVR decisions on beam times assumed to go our way.

## Spring Cosmic Run ##

### Goals (Proposal) ###

* Stable data taking using full chain (FEB, SW, Farm) and with MuPix and MuTrig

Some comments:

* Fibres should be possible with MuTrig v2 setup
* Tiles will not have a TMB ready
* For the farm, full data flow including DDR4 buffering would be the goal, a simple, e.g. hit multiplicity based selection on the GPU the stretch goal.
* To be organised in other meetings: Powering, water cooling etc.

### Before we go to PSI ###

* Can configure MuPix and MuTrig from MIDAS via FEB reliably and with a MIDAS UI. 
* *This requires either an effort by HD PI or some working hardware in Mainz for the pixels. To be clarified with HD*
* *Fibres will likely use the integration run 2021 setup*
* FEB SlowControl interface works reliably
* *Have at least a handle for further investigations starting from what we learned at the pre-Chritsmas beamtime*
* Have diagnostics for all links, PLLs and clocks in place, including MIDAS UI
* Sorter works in HW with data generators and source (also for MuTrig)
* *Looks fairly good for pixels, except for very late hits. Nik tries to simulate this week*
* We have a clear understanding how to handle 1.25 GBit link aligment, 8b/10b errors, resync etc.
* We can do run starts and configs with the ODB on the backend (i.e. not the switch and not the farm)
* *Here it is not fully clear, where the problem lies - full buffers, ODB spamming, network... To be lab tested in MZ*
* We have a list of things to achieve with priorities
* We have committments from the participating groups towards these things

### Early suff for PSI ###

* Set-up network including dedicated gateway, do performance tests
* Clear and re-cable the fibre fanout rack
* Recuperate the 2-3 fibres from the area

## Autumn Integration Run ##

* Stable data taking using full chain (FEB, SW, Farm) and with MuPix and MuTrig (all three systems) and beam
* Slow control fully interated
* Database fully integrated
* Lots of online monitoring

Some comments:
* Tile PCBs on critical path
* Two-layer online tracking woule be very cool

# Upcoming meetings #
* Next week: MAX10 firware review
* Nik will summarize plans in collaboration meeting
* In three weeks: Analyzer framework review