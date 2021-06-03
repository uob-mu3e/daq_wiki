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

* :question: What is stored in the ODB
* :ok: SPI programming
* :electric_plug: Switching board to FEB  
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

* :question: What is stored in the ODB
* :ok: SPI programming
* :electric_plug: Switching board to FEB  
* :hammer: Midas frontend  
* :interrobang: Configuration management

## Fibre readout ##

* :question: Status of the reset
* :question: Status of CRC errors
* :electric_plug: FEB receiver, decoder, unpacker
* :electric_plug: PRBS decoding
* :electric_plug: Lapse correction
* :electric_plug: Sorter  
* :ok: FEB to Switching Board


## Common readout ##

* :hammer: Data merge
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
* :hammer: Programming and monitoring of switching boards  
   *NIOS link monitoring should be available on a MIDAS custom page; Marius will work on this once firmware is ready; programming will be via a terminal*
* :hammer: Programming and monitoring of receiving boards
* :ok: Quartus licenses at PSI  

## Backend software ##

* :question: Status of the anayzers, what is still to be done?
* :interrobang: Run database
* :ok: Analyzer: Framework
* :hammer: Analyzer: Pixels
* :hammer: Analyzer: Fibres
* :hammer: Analyzer: DAQ performance

## What to test how before going nside the magnet? ##

# Future meetings

* Next in a week, also join the daylies