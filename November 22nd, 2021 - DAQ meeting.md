Present: *Cristina, Martin, Sebastian, Marius, Alex, Konrad, Heiko, Richard, Sigrid, Nik*

# Setup status #
* Cristina has a chain with FEB and SW board set up at ETH, now trying to configure the FMB in parallel to the eval board efforts in Geneva.
* Sebastian: HD has assembled two telescope DABs, status to be checked.
* Luigi also has a FEB + SW board setup.
* Konrad reports that the TMB schematics were reviewed.
* Martin will finish the optical cabling for the second clock box soon.
* Frederik will bring crate controllers to Mainz net week.

# Firmware developments #
* FEB slow control review last Wednesday. Changes implemented by Martin, pull request soon.
* Marius updated the python script for generating register documentation. There is a pull request, people will have to update their VHDL files to properly document the registers.

# Software developments #
* Register addresses for slow control will change. This can be a problem where they are hardcoded. Flag this!

# Documentation #
* See above

# Reviews #

MuPix11 starting after this. Will follow up on synthesis next week. Later: Counterpart the MuPix slow control on the FEB (Martin).