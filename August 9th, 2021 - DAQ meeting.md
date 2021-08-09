Present:

# Status of set-ups #

* Mainz: working on new Clock-Box, otherwise non-existent ( are spare functional ladders available ? / status of adapter card for telescope setup ? )
* Heidelberg Pixel:
* Heidelberg Tiles:
* Geneva:
* Zürich:

# Ongoing firmware work #
* final solution for FEB SC timing problems (MM, planned)
    * will introduce a fixed latency of 4-5 cycles to the SC reply
    * other solutions with variable latency produce to many problems in incremental read requests    
* Mutrig datapath incl. sorter 
    * MM, started but "on Hold" (busy with analysis)
    * until when do we need / want this ?
    * also changes to the sorter/sequencer needed here ?
# Ongoing software work #
* MM: changed a file format in the analysis chain:
    * analyzer_mu3e    : Midas File --> flat root file (1 hit per event)
    * analyzer_cleanup : flat root file --> root file with a vector of hits per event (containing all hits of one Midas event)