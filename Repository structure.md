## Directories

- `attic/` -> old software which is not used
- `backend_pc` -> holds the midas frontend running on the backend (power, clock/reset etc.)
    * `firmware`
        * `clock_and_reset_a10` -> not used anymore should be cleaned
        * `clock_and_reset` -> firmware for the clock and reset fpga
    * `midas_fe`
        * `MpTuneDACs` -> not used anymore should be cleaned?
        * `clock_control`
        * `environment_control`
        * `febcrate_control`
        * `network_control`
        * `power_control`
        * `raspberrypi` -> not used anymore should be cleaned
        * `xcontrol` -> not used anymore should be cleaned
    * `software` -> libraries for the frontends in midas_fe
- `common` -> contains mostly firmware and related stuff which are used over different FPGAs
    * `firmware/`
        * `assignments/` -> pin assignments for different boards
        * `registers/` -> all register used in the project
        * `a5/` -> IPs used for the a5 boards
        * `a10/`
            * `ddr` -> ips and control for DDR RAM
            * `farm` -> firmware for farm dataflow
            * `ip` -> IPs used for the a10 boards
            * `link` -> link records used on the a10 boards
            * `pcieapp` -> PCIe block
            * `swb` -> Switching Board dataflow
            * `tb` -> simulations
            * `xcvr` -> transceivers
        * `a10_tcl/` -> scripts for programming Arria 10 flash
        * `util/` -> components that do not depends on board or subsystem
        * `include/` -> NIOS software
    * `include` -> generated registers from VHDL used in software (MIDAS, etc.)
    * `kerneldriver` -> PCIe / DMA driver
    * `libmubanks` -> MIDAS events / banks definition
    * `libmudaq` -> driver for A10 connected to the PCIe / DMA driver
    * `tests` -> build tests run on the build server
    * `utils` -> scripts which dont fit anywhere else
        * `flashprog/`
        * `pixel-masking/`
    * `vhdl` -> not used anymore should be cleaned?
- `docs` -> README files most of it is not up to date or replaced by a Wiki article of the repo.
- `fe_board/` -> firmware for all different frontend boards
    * `fe/` -> should be merged with the firmware folder at some point
    * `fe_max10/`
        * `software` -> NIOS software
        * `top.vhd` -> top vhdl file for the project
    * `fe_mupix/`
        * `...`
    * `fe_scifi/`
        * `...`
    * `firmware/` -> **should** contain all the common and detector specific firmware
- `frontends` -> **should** be the place for midas_fe at the moment all is in backend_pc
- `mhttpd` -> html, js stuff
- `modules` -> submodules
    * `analyzer`
    * `googletests` -> used for scripts in common/tests folder
    * `jsroot` -> used for analyzer page in midas
- `online`
    * `sequencer` -> midas sequencer files
    * `sequencer/scifi` -> midas sequencer filse for scifi
    * `sequencer/pixels` -> midas sequencer filse for pixels
    * `sequencer/tiles` -> midas sequencer filse for tiles
    * `pixels/qctest/ladder` -> qctests
    * `scifi` -> odb setup scripts for scifi

- `switching_pc/`
    * `a10_board`/ -> dev board DDR3 RAM  setup with clock reset link for telescope setup
    * `a10_board_ddr4`/ -> dev board with DDR4 RAM setup with clock reset link for telescope setup
    * `a10_lhcb`/ -> final switching board at the moment in cosmic run mode
    * `midas_fe`/ -> MIDAS control software for the switching board
    * `slowcontrol/` -> lib for detector configuration from SWB to FEB
    * `tools/` -> folder for hardware test files running on the SWB
- `farm_pc/`
    * `a10_xcvr_example`/ -> dev board with a dummy firmware for testing
    * `farm_ddr3`/ -> FARM board with DDR3 RAM
    * `farm_ddr4`/ -> FARM board with DDR4 RAM
    * `midas_fe`/ -> MIDAS control software for the farm boards DMA / GPU readout
    * `tools/` -> folder for hardware test files running on the farm boards / GPU