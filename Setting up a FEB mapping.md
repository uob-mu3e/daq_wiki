## Crates and slots ##

* Make sure the crate controller for your crate (MSCB address and node) is set in
/ Equipment / FEBCrates / Settings / CrateControllerMSCB and
/ Equipment / FEBCrates / Settings / CrateControllerNode

* Your FEB has a global unique index between 0 and 127 - in the final system, this will be the HW address of the backplane slot. For now, it is just an index. For this index, set the crate the baord is in and the slot where it is at in
/ Equipment / FEBCrates / Settings / FEBCrate and
/ Equipment / FEBCrates / Settings / FEBSlot
for unused indices, the entries in these arrays should be 255.
So if you have FEB 3 in crate 2, slot 1, set FEBCrate[3] = 2 and FEBSlot[3] = 1

* Now you should be set for powering your FEB.

* Next we map the FEB to the switching board (assuming the central switching board here, others are similar).

* Set 
/ Equipment / LinksCentral / Settings / LinkFEB
at the offset of the link on the switching board to the global FEB index defined above. You can then also set the FEBType (Pixel, SciFi, SciTile) and FEBName of the FEB connected at that link. Finally you can set the link mask at that link to 0x3 to enable bot data and slow control.