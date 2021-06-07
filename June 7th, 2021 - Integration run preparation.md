# Agenda and Minutes

*Present: Lukas, Marius, Frederik, Martin, Alex, Luigi, Sebastian, Cristina, Yannick, Nik*

## Legend

* :ok: Ready and tested
* :electric_plug: To be integrated
* :hammer: Work ongoing
* :question: Unclear
* :interrobang: To be covered
* :beetle: Known bug
* :muscle: Extra feature, nice to have, but not critical

# Steps towards the run

## Pixel configuration ##

* :ok: What is stored in the ODB  
   *All DAC values, but not the pixel tuning is stored in the ODB*
* :ok: :hammer: SPI programming  
   *Martin is working on configuring individual mupixes* 
* :ok: Switching board to FEB  
* :hammer: Midas frontend  
* :electric_plug: Configuration management  
* :muscle: Firmware for de-multiplexing config streams allowing parallel configuration


## Pixel readout ##

* :ok: MuPix to FEB  
* :ok:FEB receiver, decoder, unpacker  
* :beetle: :question: Sorter  
   *Sends extra hits at the beginnig of the run - should be fixed, but to be tested*
* :ok: FEB to Switching Board

## Fibre configuration ##

* :ok: What is stored in the ODB  
   *All values are stored in the ODB, also many performance counters implemented*
* :ok: SPI programming
* :ok: Switching board to FEB  
* :ok: Midas frontend  
   *Lukas updated and fixed the bit-pattern generation*
* :hammer: Configuration management  
   *Configurations can be read and written to json files*

## Fibre readout ##

* :interrobang: Likely only one fibre module to be installed
* :question: Status of the reset  
   *Martin tried various options and pulse lengths for the fibre reset on Sunday, no fully staisfiyng working point found. Konrads ps-level reset shifting firmware was adapted for the Arria V and now compiles, the reset can be shifted from the NIOS menu. How to exactly use this (in combination with the PLL test) to be discussed with Konrad.*
* :question: Status of CRC errors  
   *CRC errors still there, but go away when switching to the long hit format. Seems like a feautre of the MuTrig firmware combination, was also observed by Konrad in the past. To be discussed with the MuTrig crew. Eye diagrams of the link (mattermost) look good.*
* :muscle: The PRBS test (as opposed to decoder) would be nice to have, needs input from the fibre people.
* :electric_plug: FEB receiver, decoder, unpacker
* :question: Multiplexer   
   *no news*
* :electric_plug: PRBS decoding
* :electric_plug: Lapse correction
* :electric_plug: Sorter  
   *Completion of the fibre data path will be attempted by Martin. Some support from the MuTrig commuinity would be welcome*
* :ok: FEB to Switching Board


## Common readout ##

* :electric_plug: Data merge  
   *Marius managed to merge 4 streams from on FE board ok*
* :ok: Switching board to farm
* :ok: Bank building
* :electric_plug: DDR3 and DMA
* :hammer: Midas FE  
* :electric_plug: Event building on different machine  
   *Should just work, but to be tested (also regarding serial number)*

## Infrastructure ##

* :ok: FEB programming via optical
* :ok: FEB programming via crate controller
* :ok: FEB boot from SPI flash
* :ok: FEB monitoring
* :ok: FEB control via crate controller  
    *Custom page for switching ready, crate slow control ready. Not yet linked: Link active and FEB power*
* :muscle: FEB monitoring via crate controller
* :ok: FEB control/monitoring without a NIOS terminal  
  *Pixels: NIOS is only a comfort function*  
  *Fibres: NIOS does the configuration, but can be controlled and monitored (to be tested) without terminal*
* :hammer: Programming and monitoring of switching boards  
   *NIOS link monitoring should be available on a MIDAS custom page; Marius will work on this once firmware is ready; programming will be via a terminal*
* :hammer: Programming and monitoring of receiving boards
* :ok: Quartus licenses at PSI  
* :ok: Martin created a mu3e account with a clean install of online on all relevant boxes
* :hammer: Shorter host names
* :hammer: Get crate controller ready, see [Crate Controller TODO](Crate Controller TODO)
* :hammer: Where should slow control software go - in general to online, Stefan will use a submodule

## Backend software ##

* :question: Status of the anayzers, what is still to be done?
* :hammer: Run database   
   *Frederik will set it up or find someone to set it up (Urs?)*
* :ok: Analyzer: Framework
* :hammer: Analyzer: Pixels
* :hammer: Analyzer: Fibres  
  *Much progress made by Cristina and Pirmin*
* :hammer: Analyzer: DAQ performance  
   *Maybe a MIDAS custom page with counters sufficient for the beginning*

## What to test how before going inside the magnet? ##

* Synchronisation Pixel/Pixel and Pixel/SciFi
* Data transmission on long fibres to area with all connections
* Program all FEBs when in crates, swich on and off
* Pixel configuration on cage
* Mutrig configuration on cage?

# Future meetings

* Next in a week, also join the daylies