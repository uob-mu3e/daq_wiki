# Agenda and Minutes

*Present:*


## Hardware status and to dos

In what state is the hardware, who will bring what to PSI

### DAQ
* Backplane status  
* FEB status  
* PCs:  

### Subdetectors
* Pixel DAB: 
* Tile DAB: 
* Fibre DAB:  
   
## Firmware status and to dos

What is still needed? Priorities?

* Structure of repo now ok? Documented in [Repository setup](Repository setup) and [Repository structure](Repository structure)  
* Fibre configuration (Lukas, Yannick, Cristina, no one taking full responsibility)  
   **
* Pixel frontend (Nik/Sebastian/Martin/...)
   **
* What do we need in terms of monitoring this?  
   **
* MuTrig frontends will use sorting. To be done:  
    * Receiver and channel multiplexer (Konrad)
    * PRBS decoder (Konrad, available)
    * Lapse correction, divide by 5 (Marius)
    * Sorter (Nik)  
* Fibre frontend  
   **
* Switching board firmware status (Marius)
     **  
* Farm firmware status (Marius)  
   **
* Reduced size test systems (Alex, Nik)  
* Histogramming on FEB (Pixel TS: Martin)  
   **
* FEB-sc with waitrequest (Martin)  
   **
* *FEB NIOS terminals will not be available at PSI - write MIDAS/ODB/Custom Pages now*

## Software status and to dos
* OpenSuse Leap 15.2 is recommended for all new installations
* SQL run database: Who wants to take over?  
* MIDAS  
  **
* Analyzer status [manalyzer](manalyzer Mu3e)  
   **
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
* ONGOING Fibre configuration via FEB/DAB (Lukas, Yannick)
* Fibre RO via FEB/DAB (Lukas, Yannick)
* Data chain FEB -> Switching Board -> Farm (Marius, Alex)
     * ONGOING, working with generator
* ONGOING DDR3 buffering of receiving board and bank building (Marius)
* Readout from DDR3 buffer (Marius, Nik)
* Fibre, Pixel running together (all)

# Future meetings

* Next in one week