# Agenda and Minutes

*Present: Luigi, Lukas, Alex, Marius, Martin, Sebastian, Tiancheng, Konrad, Nik*

## Hardware status and to dos

In what state is the hardware, who will bring what to PSI

### DAQ
* Backplane status  
    *Backplane so far ok except for short on the temperature measurement circuit for the FEB-off state, SPI to be tested, waiting fro firmware from Stefan*

* PCs:  
    *Mainz today received a server capable of 8x8x PCIe bifurcation. Alex will try, Nik will install Leap 14.2. Mainz considers an extra Pizza Box for Networking*

### Subdetectors
* Pixel DAB:  
    *Final DAB under production, several grounding paths foreseen. Lab version works ok, version for final detector needs more attention to grounding* 
* Tile DAB:  
    *In hand, power consupmtion as expected, to be tested further*
* Fibre DAB:  
    *Delayed components due to power loss in Texas. Mechanical constraints for final version received*
   
## Firmware status and to dos
* Discuss structure of repo (again), document in [Repository setup](Repository setup) and [Repository structure](Repository structure)  
   *Generally agreed on, some detail changes requested - please note them and other requests under the above links. Chnages will be implemented next week.*
* Remote programming of FEBs (Nik)  
   *Does now work and is reasonably fast. Please use, so we can sort out quirks*
* Pixel configuration (Luigi/Martin)  
   *Done and working, some address scheme simplification planned*
* Tile configuration (Konrad/Tiancheng)  
   *Nios software ported to new FEB, to be tested*  
* NIOS software structure:  
   *Many includes, sometimes without proper guards, no proper filtering of warnings. Alex: A lot of this due to Altera framework, but some improvements possible; will investigate*
* Fibre configuration (Lukas, Yannick, Cristina, no one taking full responsibility)  
   *Could get started on NIOS software whilst waiting for power in Texas*  
* Pixel frontend (Nik/Sebastian/Martin/...)  
   * Martin testing, finding Nik's bugs. Progress during the meeting: We get output with the right protocol, but sometimes Hit TS and subheader TS do not match*
* MuTrig frontends will use sorting. To be done:  
    * Receiver and channel multiplexer (Konrad)
    * PRBS decoder (Konrad, available)
    * Lapse correction, divide by 5 (Marius)
    * Sorter (Nik)  
       *To be done once pixel sorter is running ok*
* Switchin board firmware status (Marius)  
   *Data path working in simulation and in HW using data generator, to be tested with MuPix still this week*   
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
* Does the analyzer compile on a MaC? Try and document.

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
     * ONGOING: Path up to sorter almost fine
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

* Next in a week