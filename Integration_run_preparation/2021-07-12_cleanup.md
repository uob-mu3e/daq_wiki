Present: *Frank, Alex, Cristina, Gavin, Lukas, Marius, Martin, Sebastian, Thomas, Yannick, Nik*

# Data status and processing #

* Data were copied from switch0 and backend to merlin and to Mainz.
* RunDB was not used, esentially Marius is the run DB for the moment
* Nik will prepare a google sheet with runDB information to be filled by Marius, Luigi,...  
[Google sheet](https://docs.google.com/spreadsheets/d/1MLfoeoRalqG3xdOlihH__vh-Nz2ZcfqS7bcGl2PiqWE/edit?usp=sharing)
* Marius will produce root files with one pixel hit per event
* Thmas will work on noise removal

# Software and firmware status #

Will tag v0.12 soon. After that, there will be a development branch and regular tags with date-like names

## What are all the branches? ##

Alex does tagging/archiving and manages merging. Everyone else: Say what is in there and whether it is still needed.

* master    
* v0.12_dev  
* alex_dev  
* int_run -- MK: Pull request is done
* cherrypicking_mupix -- MM: keep until 19.07, will do a pull req next week
* sequencer_NG  -- NB: Ongoing development
* muSR_run - MM: tag, delete i think
* feb_timing_martin -- MM: keep until 19.07, will do a pull req next week
* feb_timing_nik -- MM: keep until 19.07, will do a pull req next week
* *Merged/archived: Custom_ScifiCounters*
* environment_control
* *Merged/archived: sorter_debug*
* si_sticky_flags
* daq_fixes -- NB: Is this merged? -- MK: this is fully in int_run, so if int_run is merged this can go
* setup_mhttpd
* martin_dev -- MM: keep until 19.07, will do a pull req next week
* scifisorter -- MM: is an actual active branch, work ongoing, do not delete or merge 
* *Merged/archived: fifo_rreg_patch* 
* *Merged/archived: daq_fixes_powersupplyfault*
* iv_javascript
* fe_si5345_t
* *Merged/archived: nios_memsize*
* power_multithread  -- NB: merged?
* sc_overflow_fix
* hv_control
*  *Merged/archived: custom_power*
*  *Merged/archived: environment_scripts*
*  *Merged/archived: farm_firmware_intrun*
* mutrig_datapath_tb --MM: merge & delete
* power_Frederik
* dcfifo_reg
*  *Merged/archived: scifi_to_swb*
*  *Merged/archived: time_merger_fixes*
*  *Merged/archived: mp10_slowcontrol*     -- MM: should be merged, then done 
* mp10_software_config
* *Merged/archived: programming_dev*
* odbxx_vector
* combine_HAMEGs
* feb_SC_rewrite - MM: delete, no tag needed, will start from scratch with new idea
* dev_nik -- NB: What did I do here? Merged?
* FEB_nios_bridge - MM: tag & delete, do not merge, not sure if we will need this again
* clk_reset_i2c_sequencer -- NB. merged? If not, optional development

# Where is MIDAS in the future? #

MIDAS as submodule will be removed (Lukas) and will be a prerequisite. We will have a recommended MIDAS commit for each tagged online version.

# Planned set-ups #

* Mainz: Second clock box, switching PCs, 1 FEB crate, scifi and if possible also pixels. Work on lost slow control messages, clocking stability and diagnostics, sorter, Mupix config, scifi DAQ
* ETH and Geneva: Full scifi DAQ, (SMB, FEB, Arria10) working on MuTrig configuration and operation
* HD will update on status and plans next week

# What next? #

* Please read and edit into the lessons learned document
* Also create issues in the online issue tracker for specific issues
* We try to have an in-person meeting September 22nd to 24th for disucssing the lessons learned
