# Agenda and Minutes

*Present: Alex, Cristina, Gavin, Konrad, Luigi, Lukas, Marius, Martin, Sebastian, Tiancheng*

## Hardware status and to dos

In what state is the hardware, who will bring what to PSI

### DAQ
* Backplane status  
   *Needs fixes: temperature powering, SPI MISO and MOSI swapped. FEB needs a patch to connect the board select signal, please also check midplanes of samtec connectors: Some not properly soldered*
* PCs:  
   *PC for switching board arraived, Alex working on equipping it with larger fans. 8x8x PCIe bifurcation should work.*
  
### Subdetectors
* Pixel DAB:  
    *Final DAB for spring run in production*
* Tile DAB:  
    *Two lab-DABs available, final DAB design almost complete*
* Fibre DAB:  
    *Lab-DAB just assembled*
   
## Firmware status and to dos
* Structure of repo now ok? Documented in [Repository setup](Repository setup) and [Repository structure](Repository structure)  
    *Martin will move FEB related files, Marius SW and farm realted ones, Alex the NIOS software. Commit often, careful when branching and merging in the next few days*
* Tile configuration (Konrad/Tiancheng)
   *Chain approaching completion, some issues with NIOS build system, some fixed by Alex, others we have to live with*    
* Fibre configuration (Lukas, Yannick, Cristina, no one taking full responsibility)  
   *NIOS software started*
* Pixel frontend (Nik/Sebastian/Martin/...)  
    *Luigi started with Pixel analyzer. We will save TS2 and not ToT - will have to be updated in software and SpecBook. Sorter is running as far as we know, ready for reading full ladders*
* What do we need in terms of monitoring this?
    *We will need a parallel data stream of pixel hits from before the sorter to fully validate the sorter. Which buffer exactly does the manalyzer ets its data from?*
* MuTrig frontends will use sorting. To be done:  
    * Receiver and channel multiplexer (Konrad)
    * PRBS decoder (Konrad, available)
    * Lapse correction, divide by 5 (Marius)
    * Sorter (Nik)  
       *Should be bipassable*
* Switching board firmware status (Marius)  
   *Data arriving ok, merging is being debugged*
* Farm firmware status (Marius)  
* Reduced size test systems (Alex, Nik)     
* Histogramming on FEB (Pixel TS: Martin)  
    *Martin will make use of this for a pixel hit delay histogram*
* FEB-sc with waitrequest (Martin) 
   *Martin will also connect MSCB and decouple reads. In case of conflicting writes, the optical link will have priority. If this needs to be made fully sure, use the mutex in software*

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

* Next in two weeks