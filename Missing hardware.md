#

In many test setups, not all DAQ components (e.g. clock and reset system) are present. In this case set the appropriate defines in missing_hardware.h - if the defines are defined (on, 1), then the hardware will be emulated.

Currently there are two options:

```
#!C++

#define NO_SWITCHING_BOARD 1
```
if there is now switching board, FEBs will be simulated (currently under development)

```
#!C++

#define NO_CLOCK_BOX 1
```
if there is no clock box available
