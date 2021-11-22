Present: **

# MuPix11 update#

# Setup status #
* Mainz: We might get a Mupix10, SCSI adapter card this week. 2 crate controllers arrived from PSI

# Firmware developments #
* FEB slowcontrol
    * "tree"-like slowcontrol was implemented, Pull req. is open
    * This fixed all timing problems in mupix firmware 
* SCSI Mupix FEB
    * New project started for the SCSI telescope adapter card
    * Will use a separate top file, but mostly contain existing firmware
    * could be running this week if everything goes well / if we get a mupix10
* Mupix Configuration Ideas (complete phase 1 detector, would like to discuss them at some point)
    * option1: have software looping over febs, buffer configs on FEBs (2s)
    * option2: do all the mupix chip configurations in one broadcasted transaction (0.5s)
   
* FEB programming

# Software developments #


# Documentation #


# Reviews #

Could do FEB MAX10 next week.