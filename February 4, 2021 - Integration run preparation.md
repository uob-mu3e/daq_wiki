# Agenda and Minutes

*Present: Andrea, Martin, Frederik, Yonathan, Yannick, Alex, Lukas, Tiancheng, Marius, Sebastian, Cristina, Konrad, Nik*

## Hardware status and to dos

In what state is the hardware, who will bring what to PSI

### DAQ
* Are we confident in the FEB? Produce 12 more?  
     *We wait for first tests with the Pixel DAB, possible without actual pixel sensors - decision on production next week.*
* Optical fibres: Long fibres in place at PSI, Mainz will bring fanout crates and cables for both ends
* Clock box: Mainz will bring the UCL box  
     *Mainz will provide a firmware version for the Arria X receiving board providing a clock and a reset signal - reset protocol is simple enough not to need copying form the Genesys board(ideally working without fibre patching, Alex)*
* Mainz will bring the monster PC (one switching board)
* Receiving PCs: Should we buy one more box or use Strykers? Can HD contribute boxes?  
     *Mainz will buy one more box for dual PCIe with the full switching board*
* Clarify what we need in terms of network HW
* Crate controllers are somewhat uncertain  
     *Nik will ping Stefan - Stefan needs one more day, not before next week*
* Will HD have 5 crates ready?  
     *On track in HD - would like to test with crate controller - see above.  
     HD will perform an electrical connectivity test with a DAB at the earliest convenience*

### Subdetectors
* DAB status  
      *Pixel DAB under test (Luigi)  
      Tile DAB being designed (Konrad)  
      Fibre DAB next after module board (Geneva)*
* Is there any other HW needed to read out detectors  
     *If the firmware for easy testing of FEBs (above) becomes available, no*

## Firmware status and to dos
* Remote programming of FEBs (Nik)  
   *Lab tests planned this and next week*
* Pixel configuration (Luigi/Martin)  
   *ongoing*
* Tile configuration (Konrad/Tiancheng)
   *Tiancheng starting now using old HW, transitioning to new one. Try to start from recent commits (v0.10_dev), get in touch with Mainz in case of problems (Mattermost preferred)*
* Fibre configuration (Lukas, Yannick, Cristina, no one taking full responsibility)  
    *Not much change needed relative to DESY testbeam version, Mainz will support*
* Pixel frontend (Nik/Sebastian/Martin/...)  
     *Sorting needs to be tested  
      For the current version of the sorter at 125 MHz TS, see* pull request #88
* Tile frontend (Konrad?), do we try to sort?
     *Nik will try to come up with a sorting, Nik and Marius will try to come up with a way for handling the TS counter overflow at 2**15-1*
* Fibre frontend - what do we try here?
     *Same here*
* How do we merge the timing detectors?
     *If sorted, straightforward. If not, we pretend they are sorted (Marius)*
* Merging firmware status (Marius)  
     *Merger ready for serious tests, merging per subsystem, final merging on farm.
     On the FEB it has be ensured that the fibres and tiles always send subheaders.
     Test compile for LHCb board (different speedgrade!)*
* Farm firmware status (Marius)
     *Work ongoing, DDR3 to be fully integrated, software will need a slight update for selective reading. Bank formats will closely follow DESY formats, should go to specbook, review by Nik*
* Define and implement error conditions leading to run stops (Marius, ...)     


## Software status and to dos
* Are there any architectural decisions still open?  
  *None identified*
* Will there be a database?  
  *How do we know what runs we took? Is flat MIDAS enough? Nik checks with Stefan*
* rootana build  
  *Will start with mana from scratch, port existing code. Stefan recommends manalyzer*
* what analysis should run?  
  *To be discussed later*
* data formats for saving?  
  *See above, bank format will be fixed by Marius and Nik*
* Event display (Ben)  
  *Start with that once data format is fixed*
* Alarms and soft interlocks to be defined

## Documentation
* Is this ok for documentation?  
     *For the moment yes, is lightweight and goes with the repo*


# Milestones
(no particular order)

* FEB programming via optical fibre (Nik)
     * Integrate and test SPI between MAX10 and Arria (again)
     * Write programming data via SPI
     * Write programming data to Arria via optical
     * User IF for programming
* FEB programming via MSCB (Martin, waiting for optical first)
* FEB monitoring via optical link (Nik)
     * Bank writing
     * Graphical UI
* FEB monitoring via backplane (Martin ?)
* Pixel configuration via FEB/DAB (Luigi, Martin, ...)
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

* Meeting was considered useful
+ Will be repeated biweekly until March, then maybe increase frequency