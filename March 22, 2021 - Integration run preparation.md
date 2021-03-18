# Agenda and Minutes

*Present: Stefan, Lukas, Marius, Alex, Luigi, Ben, Konrad, Sebastian, Martin, Tiancheng, Cristina, Frederik, Nik*

## Hardware status and to dos

In what state is the hardware, who will bring what to PSI

### DAQ
* Clarify what we need in terms of network HW - see pull request to spec book. Will probably not buy a 10G switch for the spring.
* Crate and crate controller in Mainz, tests so far ok.  
* HD will produce crates after Controller test.
* Mz will provide a few dozen TB of local storage in a raid.

### Subdetectors
* Pixel DAB:  
   *Luigi and Martin debuggin, so far PLL refused to lock. Resolved just after meeting (inverted reset). Signal look good already befor the equalizer.*
* Tile DAB:
   *Manufactured, on the way to HD, assembly this week, testing to start soon*
* Fibre DAB:
   *Lukas: Board is with engineers at ETH, second version started by Lukas. Where to find CAD of the cooling adaptors? Best inquire directly with Stefan Hetzel/Simon Muley at HD. Cooling adaptors come from HD if the chips are placed as for the pixels. Contact Martin for pinout questions*
   
## Firmware status and to dos
* Remote programming of FEBs (Nik)  
   *Took longer than expected, but getting there... slowly*
* Pixel configuration (Luigi/Martin)  
    *Mostly working*
* Tile configuration (Konrad/Tiancheng)  
   *To be tested with DAB*
* Fibre configuration (Lukas, Yannick, Cristina, no one taking full responsibility)  
   *To be tested with DAB*
* Pixel frontend (Nik/Sebastian/Martin/...)
   *Tests when configuration ok*
* MuTrig frontends will use sorting. To be done:
    * Receiver and channel multiplexer (Konrad ?)
    * PRBS decoder (Konrad, available)
    * Lapse correction, divide by 5 (Marius)
    * Sorter (Nik)
* Merging firmware status (Marius)  
* Farm firmware status (Marius)
* Reduced size test systems (Alex, Nik)
    * Could add clock distribution to Nik's minimal system*     
* Histogramming on FEB
    * Sebastian will provide a generic histogram for the online repo (common/firmware/util)*

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

* Next in two weeks, then maybe weekly