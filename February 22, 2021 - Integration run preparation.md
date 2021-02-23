# Agenda and Minutes

*Present: Alex, Frederik, Sebastian, Martin, Marius, Tiancheng, Ben, Konrad, Gavin, Luigi, Cristina, Nik*

## Hardware status and to dos

In what state is the hardware, who will bring what to PSI

### DAQ
*    12 more FEBs are in production - see [Schematic](https://www.physi.uni-heidelberg.de/Forschung/he/mu3e/restricted/notes/Mu3e-Note-0061-Frontenboard_v2_1_Schematic.pdf)
    * FEB v2.1 and FEB v2.0 are firmware-compatible
    * SPI clk line between the boards is fixed, but wee keep the workaround for compatibility
    * The monitored voltages are connected differently to the MAX; this needs to be handled in the MIDAS software.
* Optical fibres: Long fibres in place at PSI, Mainz will bring fanout crates and cables for both ends. Labelling scheme in [pull request to spec book](https://bitbucket.org/mu3e/mu3especbook/raw/e4fc3d0a455b86dd5800b6a5d40f0c5f89431b83/figures/CableLabellingCommissioningRun.pdf). Need to count fanout fibres needed in the counting house.
* Clock box: Mainz will bring the UCL box  
* Mainz will bring the monster PC (one switching board)
* Receiving PCs: Box ordered,monster will be receiving/backend, the new box will be switching.  
* Clarify what we need in terms of network HW - ongoing.
* Crate and crate controller on the way to Mainz.  
    *Crate has arrived, Stefan has a first controller firmware ready*
* HD will produce crates after Controller test.

### Subdetectors
* DAB status  
    *Pixel: Upstream version now also populated, config firmware being debugged. For the final DAB, intermediate board (cable change) was defined, 1-2 weeks design*  
    *Tile DAB designed, will be sent out soon*  
    *Fibre DAB at ETHZ: Clear idea of design with help from Konrad and Martin, will go to engineers*
    *QSH-doubling-up can be used for tests without backplane*  

## Firmware status and to dos
* Remote programming of FEBs (Nik)  
   *Making good progress, should have something by the end of the week*
* Pixel configuration (Luigi/Martin)
   *Martin stil debugging - documentation and MuPix8DAQ code contain bugs, now comparing waveforms, so far no success. Protocol seems fine, just speed is different*   
* Tile configuration (Konrad/Tiancheng)
    *Not much news*
* Fibre configuration (Lukas, Yannick, Cristina, no one taking full responsibility)  
   *Not much news*
* Pixel frontend (Nik/Sebastian/Martin/...)
    *Waiting for config*  
* MuTrig frontends will use sorting. To be done:
    * Receiver and channel multiplexer (Konrad ?)
    * PRBS decoder (Konrad, available)
    * Lapse correction, divide by 5 (Marius)
    * Sorter (Nik)
* Merging firmware status (Marius)  
    *Ready for tests, Alex is moving to PCIe40 board, transceivers now ok*
* Farm firmware status (Marius)
    *Banks for tiles and fibres need to be fully specified*
* Define and implement error conditions leading to run stops (Marius, ...)
    * Should be in headers/trailers when coming from the FEB, special packets to farm*
* Alex will prepare an A10 version of the clock and reset system.     


## Software status and to dos
* SQL run database: Who wants to take over?  
    *Maybe UK, maybe Frederik, should be fairly straightforward*
* Analyzer status  
    *Marius has framework and data containers ready, for MuPix also bank decoder, histograms to be done, pull request soon* 
* what analysis should run?  
* data formats for saving: Banks mostly defined
    *Check timing detectors*  
* Event display (Ben)
    *Should use analyzer framework*  
* Alarms and soft interlocks to be defined
* Farm software will read bunches of data depending on rate

## Documentation
* Please write things down here
* Also summaries of mattermost discussions


# Milestones
(no particular order)

* FEB programming via optical fibre (Nik)
     * DONE: Integrate and test SPI between MAX10 and Arria 
     * WRITTEN: Write programming data via SPI
     * ONGOING: Write programming data to Arria via optical
     * User IF for programming
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

* Next in two weeks