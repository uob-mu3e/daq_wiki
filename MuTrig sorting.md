#

Idea for MuTrig sorting:  
Essentially re-use the pixel sorter (which is still untested, mind you...)  
Requires: We have continuous, binary TS  
In turn requires: We need to do PRBS decoding and lapse correction before sorting, need to convert to a decent frequency  
Issues:  

* PRBS decoder needs a very large ROM  
* Lapse correction  
* We need to get to a good frequency (i.e. 125 MHz, which implies a divide by 5)

Rough idea:

* Use the fact that a hit takes 6 cycles (tiles) or 2.5 cycles (fibres) to arrive for a first multiplexer: 6 -> 1 for the tiles, 2 -> 1 for the fibres
* In both cases that requires three PRBS decoder inputs (2 decoder blocks ; two decoder inputs per block) (or an adventurous scheme with partitioning or running the ROM at 375 MHz) - does that fit?
* Then we somehow detect lapses and add that to decoded timestamp (can be done with a 125 MHz/increment by 5 counter)
* Then we divide the TS by 5
* The we head into the sorter; much fewer input channels than for the pixels (three for both tiles) for fibres we would have 2 inputs but two sorters one for each link. Much larger sorting depth.
* To keep the output data to 32bit we would need one more PRBS for the E part and some adders to subtract T from E on the fly. 
* More or less done...

Bonus points for:

* A clever way of dealing with the header information -> Histograms of bad hit and hittype 
* Keeping two output links busy in case of the fibres (mainly requires a change of the sequencer in the sorter) --> not needed any more since we can use two sorters one per link

Questions:

* The whole lapsing thing (solved, after some thought)
*    The memory thing (which could also be the sorting depth thing)

     The Arria V A7 has 13660 K of M10K memory (1366 blocks). The PRBS ROM should need less than 70, so that should be ok

* How expensive is the divide by 5 thing?
    [KB]: Using the LPM_DIVIDE ip (1 pipelining stage, optimize for speed):
    25ALM, 16 registers, fmax = 465MHz with 1ns input delay.