Present: *Cristina, Martin, Marius, Alex, Daniel, Nik*

# PSI beamtime preparation #
* Martin working on configuring the MuPix via the new adapter card. So far no success. Issues found: Two SPI buses, have to use the right one. LVDS repeaters have to be enabled.
* Marius and Alex are mostly done with the ArriaX - it can now send resets and clocks. Moving all lines to one QSFP seems possible but is also more work. Will patch for the PSI test beam. Clock phase looks good and can be shifted via a register.
* On the MIDAS side, some work is needed for clock and reset and also analysis. 

# Zürich Status #

Cristina is working on SPI for SciFi, somehow always gets 0 back. The module gets configured, so the the write direction is working. MISO signals are seen on the DAB. Signal strength? Something on the FPGA/NIOS? Count transition on the MISO line at the FPGA.

# Heidelberg Status #

* Daniel is working on the ethernet communication for the telescope adapter. So far reading the MAC registers does not work. The online repo Makefiles were adapted and do work.
* The next two cards are almost finished
* Some of the HSMC connections are only possible with considerable force. This is to be followed up.

# Reviews #
MAX10 review postponed