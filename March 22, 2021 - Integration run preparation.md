# Agenda and Minutes

*Present:*

## Hardware status and to dos

In what state is the hardware, who will bring what to PSI

### DAQ
* Backplane status

### Subdetectors
* Pixel DAB:  
* Tile DAB:
* Fibre DAB:
   
## Firmware status and to dos
* Discuss structure of repo (again), document in [Repository setup](Repository setup) and [Repository structure](Repository structure)
* Remote programming of FEBs (Nik)  
   *Does now work and is reasonably fast. Please use, so we can sort out quirks*
* Pixel configuration (Luigi/Martin)  
* Tile configuration (Konrad/Tiancheng)  
* Fibre configuration (Lukas, Yannick, Cristina, no one taking full responsibility)  
* Pixel frontend (Nik/Sebastian/Martin/...)
* MuTrig frontends will use sorting. To be done:
    * Receiver and channel multiplexer (Konrad ?)
    * PRBS decoder (Konrad, available)
    * Lapse correction, divide by 5 (Marius)
    * Sorter (Nik)
* Merging firmware status (Marius)  
* Farm firmware status (Marius)
* Reduced size test systems (Alex, Nik)     
* Histogramming on FEB

## Software status and to dos
* SQL run database: Who wants to take over?  
* Analyzer status [manalyzer](manalyzer Mu3e)
* what analysis should run?  
* data formats for saving: Banks mostly defined
* Event display (Ben)
* Alarms and soft interlocks to be defined

## Documentation
* Please write things down here
* Also summaries of mattermost discussions


# Milestones
(no particular order)

* FEB programming via optical fibre (Nik)
     * DONE: Integrate and test SPI between MAX10 and Arria 
     * DONE: Write programming data via SPI
     * DONE: Write programming data to Arria via optical
     * DONE: User IF for programming
* FEB programming via MSCB (Martin, waiting for optical first)
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
* Pixel sorter test (Nik + ...)
* ONGOING Tile configuration via FEB/DAB (Tiancheng, Konrad)
* Tile RO via FEB/DAB (Tiancheng, Konrad)
* ONGOING Fibre configuration via FEB/DAB (Lukas, Yannick)
* Fibre RO via FEB/DAB (Lukas, Yannick)
* Data chain FEB -> Switching Board -> Farm (Marius, Alex)
* ONGOING DDR3 buffering of receiving board and bank building (Marius)
* Readout from DDR3 buffer (Marius, Nik)
* Tile, Fibre, Pixel running together (all)

# Future meetings

* Next in a week