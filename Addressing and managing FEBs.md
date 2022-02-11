# Status quo as of February 2nd 2022 #

Each FEB currently has:

* A physical location (crate/slot). The crate controller in that crate is used to switch the power in that slot, emit resets, switch the firmware image (via BP_mode_sel) and can be used for very slow emergency programming.
* A global ID in the range 0-192, with blocks of size 48 for each switching board. This is used for addressed commands in the clock & Reset FE, in particular for enabling/disabling RO
* A port on the switching board; this corresponds to the link that is used for slow control and primary data. SciFi boards use a secondary data port. Here a lot of assumptions about the ports being contiguous are made all across the code.

In the ODB we have:

* /Equipment/FEBCrates/ - here we specify the MSCB host and MSCB node of all crate controllers. For each FEB, we specify the crate and slot. FEBs are identified by the global ID. Under Variables we have **power on/off - this should go to settings**. This is currently "owned" by the switch_fe, but should move to a separate FE on the backend (written, to be tested)
* /Equipment/Links/ - owned by the clock & reset FE. Here we have a mask and names for the four switching boards (which is needed by the clock and reset FE for run starts). There is a link mask for the FEBs (by global ID), used in the clock & reset FE for enabling/disabling FEB ro and in the switching FE for knowing which FEBs should be initialized and read out. The link mask also defines the links that correspond to data only slots for the fibre FEBs. Here we also set the FEB type (pixel, fibre, tile, fibre secondary), partly redundant with the link mask, well as FEB names. All uses the globalID. Types and Names anr only used in the switch FE. Under variables, there is an unused link status for each RX and TX link.
* /Equipment/Switching/ - here we have a bunch of UI command variables plus everything related to slow control of the FEBs as well as switching board diagnostics. Which switching board is meant at a specific time is set at compilation, the code only works with one at a time and maybe also not for anything that is not the central one. FEBs are typically identified by the Port on the Switching Board.

# Proposal to go forward #

* Manage power by a separate FE on the backend. Everything related to power goes into /Equipment/FEBCrates/
* Do we need the enable/disable via the Reset link? If we can do that via slow control (or masking on the switching board) that would all move to the switchFE
* Make four equipments and four ODB branches for the four switching boards
* Define states and state transitions for each board, make clear which FE takes care of that when and keep things consistent or check them (a board that is powered off will never talk back to you)
* FEBs will have a physical address by crate and slot (8 bits, 7 of which are needed - 4 bits slot, 3 bits crate). This will likely not be contigous and definitely not map to the switching boards.
* Add the mapping of FEBs to switching board ports in /Equipment/FEBCrates/
* Array size can be reduced to 128.
* Thus never use raw FEB indexing, but always use a feblist and a for(auto feb : febs) loop.
* Think hard wherever a FEB index maps to some other index - this code is likely broken

# Some refactoring later, February 9th 2022 #

* FE for power on the backend done and tested. Still needs a bunch of functionality to make full use of the crate controller (BP mode sel, resets, maybe firmware upload).
* Switch FE and associated slow control classes now consistently use mappedFEB. To be tested. 
* FEBlist is noncopiable
* We use references everywhere, no raw pointers (except of course to the MIDAS buffer)
* ODB changes need to be tested and propagated to the custom pages
* For things that might or might not return something (give me FEB in slot X), use std::optional

# Some rules for the future #

* Use odbxx everywhere
* Use std::string or std::string_view everywhere, string composition can be done via '+'. sprintf is deprecated. For interfacing C-style MIDAS, use .c_str()
* Pass references rather than pointers for things that should not be NULL
* Use std:option for things that can be NULL