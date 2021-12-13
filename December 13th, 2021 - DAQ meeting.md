Present: *Cristina, Haris, Alex, Marius, Daniel, Martin, Konrad, Nik*

# PSI beamtime preparation #

* Adapter card debugged, data come through and go to the PC. Source is seen.
* One link is not working.
* Getting the LVDS-links error free took a lot of tuning of the MuPix
* Clocking and resetting from the ArriaX is working
* The slow control connection still gets lost after a while (was alos observed at the integration run). The many changed components nail this down to the Arria X firmware, under investigation.
* All PLL locks and error counters now end up in registers.
* All sensors were tuned.
* Midas writing to the ring buffer is broken by a change in MIDAS, to be identified with the MIDAS team.


# Zürich Status #

* Cristina sees transitions on the SPI MISO on the FPGA, the count is not fully consitent. The NIOS is still showing 0.

# Heidelberg Status #

* Daniel is working on the connection to the ethernet PHI. Connection issues to the MAC were mostly resolved after clarifying a version mismatch in the documentation.
* Some discussion on recommended Quartus version. 18.1 is currently recommended.

# Reviews #
MAX10 review next year.

Will have a brief meeting with lessons learned from PSI next week.