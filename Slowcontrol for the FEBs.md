The FEBs are controlled and monitored from the switching boards. There is a dedicate fibre downlink from the Switching Board to the FEB, for the uplink, slow control gets merged into the main data stream on the FEB and demerged at the switching board. The PCIe readable memory is used to transfer data to the switching PC.

On the software side, the switching board is represented as a mudaq_device built on top of the kernel driver. For the slowcontrol, there is a FFSlowcontrolInterface (should later also allow MSCB-based communication).
Each switching board keeps a list of active FEBs and their mapping to the links in a feblist. The FEB and detector specific tasks are handled by the MuFEB class and its derivatives for the subdetectors. On the top level, the switching FE interfaces to MIDAS.

Each FEB will have a 16 bit slowcontrol address space. Each address can contain a 32 bit word. The available address space is distributed between the different Firmware components as follows:

(preliminary)

Total Valid Address space| | | | 0x0000-0xFFFE  
---------:| :----- | :----- | :----- | :-----:
 FEB common Block | | | | 0xFC00-0xFFFE  
 Subdetector Block | | | | 0x0000-0xFBFF  
|  Mupix: | | |  
|  |internal RAM  | | 0x0000-0x03FF  
|  |Mupix_ctrl | |  0x0400-0x0FFF  
|  |Mupix_datapath  | | 0x1000-0xFBFF
|  | | sorter | 0x1000-0x10FF  
|  | | lvds_rx | 0x1100-0x11FF  
|  Scifi/Scitile: | | |   
|  |internal RAM | | 0x0000-0x3FFF  
|  |scifi regs | |  0x4000-0xFBFF