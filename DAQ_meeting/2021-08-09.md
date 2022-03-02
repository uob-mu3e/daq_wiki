Present: *Martin, Alex, Cristina, Gavin, Thomas, Nik*

# Status of set-ups #

* Mainz: working on new Clock-Box, otherwise non-existent ( are spare functional ladders available - Thomas: Maybe ladder 30 / status of adapter card for telescope setup - no news, might be a while ) Gateway PC arrived and smoke-tested ok
* Heidelberg Pixel: No news on setups
* Heidelberg Tiles: No news
* Geneva: No news
* Zürich: Waiting for extra DAB production

# Ongoing firmware work #
* final solution for FEB SC timing problems (planned)
    * will introduce a fixed latency of 4-5 cycles to the SC reply
    * other solutions with variable latency produce to many problems in incremental read requests    
* Mutrig datapath incl. sorter 
    * started but "on Hold" (busy with analysis)
    * until when do we need / want this? - after pixel sorter is tested
    * also changes to the sorter/sequencer needed here? - yes
# Ongoing software work #
* changed a file format in the analysis chain:
    * analyzer_mu3e    : Midas File --> flat root file (1 hit per event)
    * analyzer_cleanup : flat root file --> root file with a vector of hits per event (containing all hits of one Midas event)
* analyzer optimization: from 15min/GB to 2min/GB
* Thomas reporting on correlation search, so far not much seen. Should look at low level properties of files. 

Next meeting in one or two weeks, depending on analysis progress