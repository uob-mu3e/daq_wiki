Present: *Daniel, Alex, Cristina, Martin, Luigi, Marius, Haris, Sebastian, Nik*

# MuPix11 update#

# Setup status #
* Mainz: We will get a Mupix10, SCSI adapter card this week. 2 crate controllers arrived from PSI
* Luigi has an integration-run like DAQ setup at Heidelberg and is investigating the MuPix temeprature measurement which gave inconsisten readings between up- and downstream during the integration run.
* Sebastian reports that probe testing of the FEB-Telescope-Adapter-Card looks good. Pinouts were exchanged with Martin.
* No news concerning DAQ from Zürich
* Cristina has removed kapton insulation from micro-twisted pair cables using Silvan's molten acid setup at PSI. Setup is availabe for further tests.
 
# Firmware developments #
* FEB slowcontrol (Martin)
    * "tree"-like slowcontrol was implemented, Pull req. is open
    * This fixed all timing problems in mupix firmware 
* SCSI Mupix FEB (Martin, Daniel)
    * New project started for the SCSI telescope adapter card
    * Will use a separate top file, but mostly contain existing firmware
    * could be running this week if everything goes well / if we get a mupix10
    * Sebastian mentions slight changes to the configuration wiring, which allows for parallel configuration of e.g. the telescope
* Mupix Configuration Ideas (complete phase 1 detector, Martin)
    * option1: have software looping over febs, buffer configs on FEBs (2s)
    * option2: do all the mupix chip configurations in one broadcasted transaction (0.5s)
    * Option one is prefered.   
* FEB programming
    * Nik thinks he can fit two images into the SPI-Flash, including an emergency one. Will need to be tested.
* Martin and Daniel will discuss FEB firmware for the etelescope adapter

# Software developments #
* Software for the FEB+Adapter telescope should use MIDAS

# Documentation #
* Marius will review the register documntation again, should be merged also with missing parts.

# Reviews #
Will do FEB MAX10 next week, maybe also some MuPix11 issues.