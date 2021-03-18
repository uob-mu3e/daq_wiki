Here we list what should go where in the online repo, naming conventions etc.

# Overall structure #
On the top level, the repository is structured by the hardware on which software and firmware is running, namely:

* **fe_board**: Front-end board firmware and NIOS software
* **switching_pc**: Switching board firmware and NIOS software, MIDAS code for switching baord, FEB and detector slow control.
* **farm_pc**: Receiving board firmware and NIOS software, MIDAS code for data readout, GPU code
* **backend_pc**: Event building MIDAS code, firmware and MIDAS code for the clock and reset system, MIDAS code for network control, powering

And directories with service functions:

* **common**: Constants such as register addresses needed on several PCs/boards, common firmware and software parts (should we move those to 'util')?
* **docs**: Documentation, should probaly be merged with this wiki (have a submodule always pointing to the wiki head?)
* **mhttpd**: Custom websites and java script
* **attic**: temporary storage for files obsoleted by refactorings
* **install**: Default position for executables and libraries
* **modules**: Softwer from separate repos such as MIDAS or the analyzer
* **online**: Fiel fromwhich things are run, containing startup scripts etc.


### Currently misplaced/orphaned directories ###

* 'backend_pc/midas_fe/raspberrypi' where does that belong?
* 'backend_pc/midas_fe/MpTuneDACs' should probably go to the switching pc
* 'frontends' is this just a relic than can go?

# Directory structure #

[Repository structure](Repository structure)