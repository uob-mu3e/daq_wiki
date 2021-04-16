# Agenda and Minutes

*Present: Alex, Cristina, Luigi, Lukas, Martin, Sebastian, Marius, Nik*

## Hardware status and to dos

In what state is the hardware, who will bring what to PSI

### DAQ
* Backplane status  
   *Should arrive in HD these days*
* FEB status (ZH board?)  
   *PCBs arrived back side populated in HD. ZH board seems to be ok (male SMA plug is a pain, JTAG is very painful)*
* PCs:  
   *Alex has the PCIe40 board running with the new box including new fans*
  
### Subdetectors
* Pixel DAB:  
    *Final version arrived, to be tested*
* Tile DAB:  
    *No report*
* Fibre DAB:  
    *Tests will continue once HW and PCs issues resolved. Temperature readout working*
   
## Firmware status and to dos
* Structure of repo now ok? Documented in [Repository setup](Repository setup) and [Repository structure](Repository structure)  
    *Alex has moved all software, Marius is happy with the switching board and farm firmware, Martin will now move the FEB firmware*
* Tile configuration (Konrad/Tiancheng)   
* Fibre configuration (Lukas, Yannick, Cristina, no one taking full responsibility)  
* Pixel frontend (Nik/Sebastian/Martin/...)
    *Pixel readout is possible, data coming out does not yet look ok. Some more diagnosis tools needed. Also: Channel masking. Bank reading for the analyzer has to be redone for the format from the switching board.*  
* What do we need in terms of monitoring this?
* MuTrig frontends will use sorting. To be done:  
    * Receiver and channel multiplexer (Konrad)
    * PRBS decoder (Konrad, available)
    * Lapse correction, divide by 5 (Marius)
    * Sorter (Nik)  
* Switching board firmware status (Marius)  
   *Lab readout is working, Marius implemented new bank formats, merger is being debugged*
* Farm firmware status (Marius)  
    *see above*
* Reduced size test systems (Alex, Nik)     
* Histogramming on FEB (Pixel TS: Martin)  
* FEB-sc with waitrequest (Martin)  
   *Being simulated*

## Software status and to dos
* OpenSuse Leap 15.2 is recommended for all new installations
* SQL run database: Who wants to take over?  
* Analyzer status [manalyzer](manalyzer Mu3e)
* what analysis should run?  
* data formats for saving: Banks mostly defined
* Event display (Ben)
* Alarms and soft interlocks to be defined
* Does the analyzer compile on a MaC? Try and document.  
   *Marius suceeded, needs some care with root and other packages to install. Cristina will try*

## Documentation
* Please write things down here
* Also summaries of mattermost discussions
* Very nice documentation of the test setup: [FEB to A10 Dev Board Lab Setup](FEB to A10 Dev Board Lab Setup)


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