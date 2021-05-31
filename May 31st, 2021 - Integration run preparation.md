# Agenda and Minutes

*Present: Alex, Lukas, Marius, Martin, Yannick, Pirmin, Cristina*

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

*Martin: generate header files for midas fontends and NIOS from register VHDL, still to be done for MuPix part*

* :ok: SPI programming
* :electric_plug: Switching board to FEB  
    *Typically not used*
* :hammer: Midas frontend  
    *UI missing, Luigi wanted to take care, Martin getting started*
* :electric_plug: Configuration management  
    *Can use existing git repo, need to integrate with UI*
* :muscle: Firmware for de-multiplexing config streams allowing parallel configuration

## Pixel readout ##

* :ok: MuPix to FEB  
* :ok:FEB receiver, decoder, unpacker  
* :beetle: :question: Sorter  
   *Sends extra hits at the beginnig of the run - should be fixed, but to be tested*
* :ok: FEB to Switching Board

## Fibre configuration ##

* :ok: SPI programming
    *Works with DAB v2*
* :electric_plug: Switching board to FEB  
   *Bugs in RPCs found and figed, to be tested*
* :hammer: Midas frontend  
   *Cristina started a custom page for configuration*
* :interrobang: Configuration management

## Fibre readout ##

* :ok: :question: :bug: MuTrig to FEB  
    * Seems to work, but CRC errors seen. Also, pinout problems for half the module"
* :electric_plug: FEB receiver, decoder, unpacker
* :electric_plug: PRBS decoding
* :electric_plug: Lapse correction
* :hammer: Sorter  
    *Compiles, simulation soon. Can be integrated*
* :ok: FEB to Switching Board


## Common readout ##

* :hammer: :bug: Data merge
    *Naming scheme fixed, one known bug to be tackled:
* :ok: Switching board to farm
* :ok: Bank building
* :electric_plug: DDR3 and DMA
* :hammer: Midas FE  
   *Word based reading should be ok, ringbuffer and subheader based to be fully done. Control of request FIFO to be done. To be clarified what the serial number does.*
* :electric_plug: Event building on different machine  
   *Should just work, but to be tested (also regarding serial number)*

## Infrastructure ##

* :ok: FEB programming via optical
* :ok: FEB programming via crate controller
* :ok: FEB boot from SPI flash
* :ok: FEB monitoring
* :hammer: FEB control via crate controller
* :muscle: FEB monitoring via crate controller
* :hammer: Programming and monitoring of switching boards  
   *NIOS link monitoring should be available on a MIDAS custom page; Marius will work on this once firmware is ready; programming will be via a terminal*
* :hammer: Programming and monitoring of receiving boards
* :ok: Quartus licenses at PSI  
   *Five licenses available on mu3eBackend*

## Backend software ##

* :interrobang: Run database
* :ok: Analyzer: Framework
* :hammer: Analyzer: Pixels
* :hammer: Analyzer: Fibres
* :hammer: Analyzer: DAQ performance

# Future meetings

* Next in a week, also join the daylies