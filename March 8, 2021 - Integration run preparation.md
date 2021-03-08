# Agenda and Minutes

*Present: *

## Hardware status and to dos

In what state is the hardware, who will bring what to PSI

### DAQ
* Clarify what we need in terms of network HW - see pull request to spec book. Will probably not buy a 10G switch for the spring.
* Crate and crate controller in Mainz, tests so far ok.  
* HD will produce crates after Controller test.

### Subdetectors
* DAB status  
   
## Firmware status and to dos
* Remote programming of FEBs (Nik)  
   *Took longer than expected, but getting there*
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
     * ONGOING: Write programming data to Arria via optical
     * DONE: User IF for programming
* FEB programming via MSCB (Martin, waiting for optical first)
* FEB monitoring via optical link (Nik)
     * ONGOING: Bank writing
     * ONGOING: Graphical UI
* FEB monitoring via backplane (Martin ?); might be delayed to after the spring run
* ONGOING Pixel configuration via FEB/DAB (Luigi, Martin, ...)
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

* Next in two weeks?