Setup in the back corner of the Mainz lab end of February, allows for most features (- run starts)

# Ingredients #

* 1 Stryker
* 1 Arria10 Board (here the DDR3 version)
* 1 FEB
* 1 Si5433 Eval Board
* 1 Windows Laptop
* 1 Firefly B04
* 3 SMA cables
* 1 USB A to B cable
* 1 micro USB cable
* 1 MTP Female Male Cable (Female/Female for the fireflies with flat heatsinks and male cables)
* 1 MTP up to MTP down connector
* At least one programming cable

# Clocking #

Configure the clock eval board to produce a LVDS 125 MHz clock for the FEB (2 SMA cables) and a 2.5 V CMOS clock for the Arria 10 board.  
Make sure the FEB Arria is configured to use the LVDS input clock (comment line 7 and uncomment line 9 in online/fe_board/fe/software/app_src/si5345_fe_v2.h), build and upload the app.

# ODB #

If you directly connect the FEB and the left QSFP on the Arria 10 board, the FEB will be at channel 0. Put a 3 in the link mask and set the FEB type.