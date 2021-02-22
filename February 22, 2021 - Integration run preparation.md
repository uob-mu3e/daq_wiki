# Agenda and Minutes

*Present:*

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
* HD will produce crates after Controller test.

### Subdetectors
* DAB status  

## Firmware status and to dos
* Remote programming of FEBs (Nik)  
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
* Define and implement error conditions leading to run stops (Marius, ...)     


## Software status and to dos
* SQL run database: Who wants to take over?  
* Analyzer status
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
* Tile configuration via FEB/DAB (Tiancheng, Konrad)
* Tile RO via FEB/DAB (Tiancheng, Konrad)
* Fibre configuration via FEB/DAB (Lukas, Yannick)
* Fibre RO via FEB/DAB (Lukas, Yannick)
* Data chain FEB -> Switching Board -> Farm (Marius, Alex)
* DDR3 buffering of receiving board (Marius)
* Readout from DDR3 buffer (Marius, Nik)
* Tile, Fibre, Pixel running together (all)

# Future meetings

* Next in two weeks