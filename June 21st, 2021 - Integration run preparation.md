# Agenda and Minutes

*Present:*

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

* :ok: SPI programming  
* :ok: Switching board to FEB  
* :ok: Midas frontend  
* :electric_plug: Configuration management  
* :muscle: Firmware for de-multiplexing config streams allowing parallel configuration

## Pixel readout ##

* :ok: MuPix to FEB  
* :ok:FEB receiver, decoder, unpacker  
* :ok: :question: Sorter  
   *Sends extra hits at the beginnig of the run - should be fixed, but to be tested*
* :ok: FEB to Switching Board

## Fibre configuration ##

* :ok: SPI programming
* :ok: Switching board to FEB  
* :ok: Midas frontend  
* :hammer: Configuration management  

## Fibre readout ##

* :question: Status of the reset  
* :question: Status of CRC errors  
* :muscle: The PRBS test (as opposed to decoder) would be nice to have, needs input from the fibre people.
* :electric_plug: FEB receiver, decoder, unpacker
* :question: Multiplexer   
* :electric_plug: PRBS decoding
* :electric_plug: Lapse correction
* :electric_plug: Sorter  
* :ok: FEB to Switching Board


## Common readout ##

* :ok: Data merge  
* :ok: Switching board to farm
* :ok: Bank building
* :electric_plug: DDR3 and DMA
* :hammer: Midas FE  
   *MIDAS page with counters now available*
* :electric_plug: Event building on different machine  
   *Should just work, but to be tested (also regarding serial number)*

## Infrastructure ##

* :ok: FEB programming via optical  
* :hammer: FEB programming via crate controller   
* :ok: FEB boot from SPI flash
* :ok: FEB monitoring
* :ok: FEB control via crate controller  
* :muscle: FEB monitoring via crate controller
* :ok: FEB control/monitoring without a NIOS terminal  
* :hammer: Programming and monitoring of switching boards  
* :hammer: Programming and monitoring of receiving boards
* :ok: Quartus licenses at PSI  
* :ok: Martin created a mu3e account with a clean install of online on all relevant boxes
* :hammer: Shorter host names
* :hammer: Get crate controller ready, see [Crate Controller TODO](Crate Controller TODO)
* :hammer: Where should slow control software go - in general to online, Stefan will use a submodule

## Backend software ##

* :question: Status of the anayzers, what is still to be done?
* :ok: Run database   
* :question: Run database interface
* :ok: Analyzer: Framework
* :hammer: Analyzer: Pixels
* :hammer: Analyzer: Fibres  
  *Much progress made by Cristina and Pirmin*
* :hammer: Analyzer: DAQ performance  
   *Maybe a MIDAS custom page with counters sufficient for the beginning. That page is available*

## What to test how before going inside the magnet? ##

* Synchronisation Pixel/Pixel and Pixel/SciFi  
    *Use Sr90 to trigger to pixel chips behind each other*
* Data transmission on long fibres to area with all connections  
   *Once cage is in the area*
* Program all FEBs when in crates, switch on and off  
   *Waiting for crate controllers*
* Pixel configuration on cage  
   *Looks ok*
* Mutrig configuration on cage  
   *Ongoing*

# Future meetings

* Next in a week, also join the daylies