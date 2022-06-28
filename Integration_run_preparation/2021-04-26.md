# Agenda and Minutes

*Present: Luigi, Lukas, Alex, Cristina, Frederik, Gavin, Konrad, Marius, Martin, Sebastian, Tiancheng, Yannick, Yonathan, Thomas, Nik*


## Hardware status and to dos

In what state is the hardware, who will bring what to PSI

### DAQ
* Backplane status  
    *Fine as far as tested, all produced*
* FEB status  
    *Undergoing smoke tests in HD, to be shipped to Mainz for full testing and assembly*
* PCs:  
   *Another server ordered as a network gateway (MZ)*
* *Mainz will bring a big scope to PSI*

### Subdetectors
* Pixel DAB: 
   *Pinout issue fixed, now working as expected; fibre and tile DAB pinouts should be double checked (Martin plus subdetector experts)* 
* Tile DAB: 
   *Critical errors in TMB found, I2C working, more to be seen* 
* Fibre DAB:  
  *Lukas sees errors when configuring via SPI; can likely be fixed by changing NIOS SPI configuration*
   
## Firmware status and to dos

What is still needed? Priorities?

* Structure of repo now ok? Documented in [Repository setup](Repository setup) and [Repository structure](Repository structure)  
   *FEB directories still to be unified (Martin, not highest priority)*
* Tile configuration (Konrad/Tiancheng)   
   *see above*
* Fibre configuration (Lukas, Yannick, Cristina, no one taking full responsibility)  
   *see above*
* Pixel frontend (Nik/Sebastian/Martin/...)
   *Hits missing in columns with specific bit pattern, not understood, seems to happen early on the FEB*
* What do we need in terms of monitoring this?  
   *Foresee hit counters everywhere*
* MuTrig frontends will use sorting. To be done:  
    * Receiver and channel multiplexer (Konrad)
    * PRBS decoder (Konrad, available)
    * Lapse correction, divide by 5 (Marius)
    * Sorter (Nik)  
      *Will start on a prototype soon*
* Fibre frontend  
   *Cristina debugging FEB-Arria10 connection*
* Switching board firmware status (Marius)
     *Merger to be tested with two FEBs this week, code review on Wednesday*  
* Farm firmware status (Marius)  
   *Being assembled, also to be reviewed*
* Reduced size test systems (Alex, Nik)  
* Histogramming on FEB (Pixel TS: Martin)  
   *no news*
* FEB-sc with waitrequest (Martin)  
   *no news*
* *FEB NIOS terminals will not be available at PSI - write MIDAS/ODB/Custom Pages now*

## Software status and to dos
* OpenSuse Leap 15.2 is recommended for all new installations
* SQL run database: Who wants to take over?  
* MIDAS  
  *Double copy from DMA required, can we run this in ring buffer mode?*
* Analyzer status [manalyzer](manalyzer Mu3e)  
   *Marius found some bugs in the data decoder - please use the provided test framework!*
* what analysis should run?  
* data formats for saving: Banks mostly defined
* Event display (Ben)
* Alarms and soft interlocks to be defined

## Documentation
* Please write things down here
* Also summaries of mattermost discussions

# Other

# Milestones
(no particular order)

* FEB programming via optical fibre (Nik)
     * DONE: Integrate and test SPI between MAX10 and Arria 
     * DONE: Write programming data via SPI
     * DONE: Write programming data to Arria via optical
     * DONE: User IF for programming
* FEB programming via MSCB/Crate Controller (Nik, Stefan)
* FEB monitoring via optical link (Nik/Martin)
     * DONE: Bank writing
     * DONE: Graphical UI
     * ONGOING : Firefly monitoring
* FEB monitoring via backplane (Martin/Stefan/Nik); might be delayed to after the spring run
     * ONGOING: Backplane SPI testing
     * ONGOING: Interface for switching FEBs on or off
* ONGOING Pixel configuration via FEB/DAB (Luigi, Martin, ...)
     * DONE: Firmware part
     * ONGOING: MIDAS integration of many configurations (Luigi)
* Pixel RO via FEB/DAB (Luigi, Martin, ...)
     * DONE: Path up to SW-Board fine
* Pixel sorter test (Martin, Nik)
     * ONGOING debugging of details
* ONGOING Tile configuration via FEB/DAB (Tiancheng, Konrad)
* Tile RO via FEB/DAB (Tiancheng, Konrad)
* ONGOING Fibre configuration via FEB/DAB (Lukas, Yannick)
* Fibre RO via FEB/DAB (Lukas, Yannick)
* Data chain FEB -> Switching Board -> Farm (Marius, Alex)
     * ONGOING, working with generator
* ONGOING DDR3 buffering of receiving board and bank building (Marius)
* Readout from DDR3 buffer (Marius, Nik)
* Tile, Fibre, Pixel running together (all)

# Future meetings

* Next in one week