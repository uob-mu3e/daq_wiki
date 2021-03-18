## Directories
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
- `lib/` (old common)
    * `firmware/`
        * `assignments/` (pin assignments for different boards)
        * `registers/` (all register used in the project)
        * `constants/` (all constants used in the project)
        * `a5/`
            * `ip/` (Arria V IPs)
            * `tb/` (simulation)
            * `xcvr, etc.`
            * `MuPix/`
                * `tb/` (simulation)
                * `...`
            * `Scifi/`
                * `tb/` (simulation)
                * `...`
            * `Tile/`
                * `tb/` (simulation)
                * `...`
            * `common/` (stuff which is used on more than 1 board type)
                * `tb/` (simulation)
                * `MuTrig/`?
                * `Sorter/`
                    * `tb/` (simulation)
                    * `...`
                * `...`
        * `a10/`
            * `ip/`
            * `tb/` (simulation)
            * `xcvr, hex2seg7, etc.`
            * `SWB/` 
                 * `ip/` (SWB IPs)
                 * `tb/` (simulation)
            * `Farm/` (FEB components)
                 * `ip/` (SWB IPs)
                 * `tb/` (simulation)
        * `util/` (components that do not depends on board or subsystem)
        * `ips/` (ips that are used on more than one board)
        * `include/` (NIOS software)
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