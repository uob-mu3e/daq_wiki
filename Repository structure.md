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
- `fe_board/`
    * `fe_malibu/`
        * `software/`
            * `app_src/`
            * `include` -> lib/firmware/include/
        * `top.vhd`
        * `top.qsf` (links to include.qip files)
        * `Makefile`
    * `fe_max10/`
        * `...`
    * `fe_mupix/`
        * `...`
    * `fe_scifi/`
        * `...`

- `switching_pc/`
    * `SWB_0`/
        * `software/`
            * `app_src/`
            * `include` -> lib/firmware/include/
        * `top.vhd`
        * `top.qsf` (links to include.qip files)
        * `Makefile`
    * `SWB_0`/
        * `...`
    * `SWB_2`/
        * `...`
    * `SWB_3`/
        * `...`
    * `A10_dev`/
        * `...`
- `farm_pc/`
    * `A10_dev`/
        * `...`

## Comments

- [AK] It is now possible to set the values of `SRC_DIR` in `Makefile`,
  which allows to put sources directly into `software/` directory (instead of `software/app_src/`).
  This can also be used as default.
- [AK] how about removing FE v1 firmware, and using `fe/mupix`, `fe/scifi`, `fe/tiles`, `fe/max10` dir names
- [AK] I would move `firmware/a5/common` to `firmware/common`, and also move `firmware/a10/{swb,farm}` to `firmware/{swm,farm}`
- [AK] also, I suggest using small case for directories, e.g. `mupix` instead of `Mupix`