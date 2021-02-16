Idea for MuTrig sorting:  
Essentially re-use the pixel sorter (which is still untested, mind you...)  
Requires: We have continuous, binary TS  
In turn requires: We need to do PRBS decoding and lapse correction before sorting, need to convert to a decent frequency  
Issues:  

* PRBS decoder needs a very large ROM  
* Lapse correction might or might not require a 625 MHz counter (when does the MuTrig generate a frame)  
* We need to get to a good frequency (i.e. 125 MHz, which implies a divide by 4)

Rough idea:

* Use the fact that a hit takes 6 cycles (tiles) or three and a bit cycles (fibres) to arrive for a first multiplexer: 6 -> 1 for the tiles, 3 -> 1 for the fibres
* In both cases that requires three PRBS decoders (or an adventurous scheme with partitioning or running the ROM at 375 MHz) - does that fit?
* Then we somehow detect lapses and add that to decoded timestamp
* Then we divide the TS by 5
* The we head into the sorter; much fewer input channels than for the pixels (three for both tiles and fibres), but much larger sorting depth.
* More or less done...

Bonus points for:

* A clever way of dealing with the header information
* Keeping two output links busy in case of the fibres (mainly requires a change of the sequencer in the sorter)

Questions:

* The whole lapsing thing
* The memory thing (which could also be the sorting depth thing)
* How expensive is the divide by 5 thing?