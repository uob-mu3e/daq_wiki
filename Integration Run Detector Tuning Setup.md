# Requirements #

* TDK Power for HV boxes and FEBs
* [Si5338 clock board](https://www.silabs.com/documents/public/user-guides/Si5338-EVB.pdf) inside downstairs rack
* ROOT 6 with CXX > 14
* Linux Kernel > 4.12
* Quartus

# Installation Hardware #
## Clock Setup Farm & LHCb Board##

* CLK2A goes to the LHCb Board, CLK3A and 3B go to the two farm PCs. 
* All outputs should be 125 MHz 3.3V LVCMOS
* The octagonal board drives inputs 5 & 6, all other inputs are not functional on the board that's currently installed.
* The octagonal board needs to be powered by the bench top power supply, the Si evaluation board needs to be powered by the USB hub and programmed by a windows laptop as specified above. For this, you need to use ClockBuilder Desktop 6.5, **NOT** the usual ClockBuilder Pro.

![B865EB4A-BAD9-4B2C-8D37-9E639390678F.jpg](https://bitbucket.org/repo/7zKBgbq/images/884970373-B865EB4A-BAD9-4B2C-8D37-9E639390678F.jpg)

It should be in a running state already.

## FEBs ##

The fibre layout can be found at the wall in the downstairs hut. The fibres from the area are patched in the yellow rack on the Aare side (see below).

![IMG_1607.JPG](https://bitbucket.org/repo/7zKBgbq/images/2155823138-IMG_1607.JPG)

Users typically don't need to change anything here.

## MSCB Submasters ##

The HV boards and crate controllers are controlled via MSCB. There are optical receivers inside the magnet, which are connected to a counterpart inside the downstairs hut, which is controlled by an MSCB submaster. You can find the MSCB software [here](https://bitbucket.org/tmidas/mscb). 

# Power everything on #

* Your FEB(s)
* Your detector
* Don't forget the chillers/helium system

# Which boards/PCs to use #

For tuning, we skip the farm and run on the switching PC mu3eSwitch0 directly. 

========================

# Installation Software #

* `git clone git@bitbucket.org:mu3e/online.git`
* `git checkout DEV-BRANCH`
* `git submodule update --init --recursive`
* `mkdir build`
* `cd build`
* `cmake ..`
* `make`
* `make install`

# Compile A10 Hardware #

* A basic A10 board file is stored at <https://seafile.rlp.net/d/399ebc0f7e5b49d59522/> at `Mu3e Firmware/SWB/ SWB_debug_sof_file/top_signaltap.sof`
* Download this file and navigate to `online/switching_pc/a10_board/`
* Connect the A10 board via a USB cable to you PC and execute `jtagconfig` and check if the device is showing up
* `make SOF=PATH_TO_top_signaltap.sof pgm`
* (If you see a folder called generated remove it before you continue)
* `make` 
* `make app_upload`
* `make terminal`
* Now the NIOS terminal of the A10 board should show up (TODO: add picture)
* Close this terminal again and navigate to `common/kerneldriver`
* `make` for compiling the kernel modules
* The following lines are only possible if the A10 was flashed with a PCIe firmware before (see Flash A10 board) and you need to redo them after you programmed the device via `make pgm`
* Since the device is reprogrammed we have to rescan the PCIe devices.
* First we need the find the device number `sudo lspci | grep Altera` -> "dev_number" Unassigned class [ff00]: Altera Corporation Device 0004 (rev 01) 
* Then we need to remove this device and rescan it.
* `sudo su` in the `common/kerneldriver` folder
* `echo 1 > /sys/bus/pci/devices/0000:"dev_number"/remove`
* `echo 1 > /sys/bus/pci/rescan`
* Load the FPGA driver with `./load_mudaq.sh`
* Now you should have two devices under `/dev/mudaq*`. One is the FPGA the other one the DMA buffer.
* Change the permissions of the devices so a normal user can use them `chmod go+rw /dev/mudaq*`

# Test A10 Device #

* If the A10 device showed up correctly a view tests can be performed to check wheaten the device is working
* Navigate to the build directory 
* First lets check the PCIe registers 
* `./farm_pc/tools/rw rr 0x1` -> should show a hex value != 0x0
* Now lets try to readout the DMA buffer with generated data
* `./farm_pc/tools/swb_dmatest 2 0 0` -> when to program enters the write file state you can kill it with `ctrl+c`
* Check the output of `head memory_content.txt` should be different from 0x0 for the data
* If all of this works you can continue 

# Flash A10 Board (optional) #

* If the board is used the first time a factory firmware is loaded when starting the FPGA.
  Since the FPGA is used as a PCIe device a custom firmware need to be loaded to this flash
  so the device can be recognized as a PCIe device.
* Run the commands from Compile Hardware for the A10 board
* Open the flash GUI to flash the sof file (firmware configuration)
  and elf file (software for the NIOS) to the A10.
  `./common/firmware/a10_tcl/program_gui.sh`
  (during flashing the sof will be converted to binary format,
  split into parts of 256KB and flashed, the total number of parts is about 170,
  you should see in the console that parts are flashed one by one
  and it should take several minutes to complete)
  ![7DF405AF-3C31-40D9-8CE5-256CC26F4949.jpeg](https://bitbucket.org/repo/7zKBgbq/images/3249624293-7DF405AF-3C31-40D9-8CE5-256CC26F4949.jpeg)
* Choose the sof file and elf file you want to flash to the device and execute the flashing.
* Make sure that the switches on the Board are placed correctly
  otherwise the custom firmware will not be loaded
  (the dis switches are located between fpga chip and pcie edge connector,
  all switches hava to be set to 0 position - in the direction of fpga chip)
  (TODO: add picture)
* After power cycling the board (restart PC), the firmware will be loaded from flash.

# Compiling and connecting the FEB #

* goto `online/fe_board/your_subdetector` and execute
* `make flow`
* goto `online/fe_board/fe/software/app_src`, open `si5345_fe_v2.h` and select your clk source in lines 7-9
    * if you want to run without the A10 board, select "free running"
    * if you want to use the A10, but you don't have a optical clock distribution, select "lvds" and connect the lvds clock to CON4 and CON5 if the FEB
    * if you have optical clock distribution, leave the selection on "optical"
* go back to `online/fe_board/your_subdetector`
* `make app`
* you might consider to put some cooling solution (office ventilator etc.). The firefly modules (between jtag and sma) can get really hot.
* if you want to connect to the A10:
    * you need to put a BIDIRECTIONAL !! Firefly into the slot closer to the Jtag header.
    * line 12 of the MTP cable needs to connect to line 1 of the MTP on the Arria10
    * if you want to provide an optical clock, do so on line 10 of the MTP cable
    * if you do not want to provide an optical clock, you can connect directly to the arria10 with a male-female MTP12 cable, (female-female will not work, male-male will break things)
    * make sure that you connect rx with tx lines (you can check this once the feb is powered by using a smartphone camera to look at the optical connectors. Do not look into them directly !)
* power the FEB board, 15V, 0.8 A if nothing is connected. If you have optical transceivers and subdetectors connected you have to increase the current limit (for pixel FEB roughly 1.3 A)
* Now connect a USB-blaster to the Jtag Header (the one closer to the SMA connectors) and run `jtagconfig`
* if the device does not show up in the jtagconfig output, disconnect the usb cable, connect the USB cable again, run jtagconfig again.
* repeat previous step until the device shows up (please do not do this slowly, you could need 20-30 repetitions)
* `make pgm`
* `make app_upload`
* `make terminal`
* the processor (nios) on the FEB will need a few seconds to boot, afterwards you should end up in the main menu
* if you do not see the main menu or you disconnected at some point and want to reconnect, press Enter after `make terminal` to print menu again, the processor will only automatically print the main menu on boot.
* if you have the Arria10 connected and configured according to the steps above, you can go into the firefly menu now and check if you see "BC" on channel 0 of the FEB. You should do the same on the Arria, the menu there is called "xcvr". If you don't see "BC" on both sides, something with the optical connection or the clock is wrong. Check with a scope if both clock sources are synchronised in this case.
* go to the reset menu on the nios and put the FEB into the idle state (If it booted into RESET, press "7")
* if you have problems to put the FEB into idle, exit the nios-terminal and repeat from `make app_upload`
* configure your subdetector using your software on the nios (or from midas)
* To start to send data go to the reset menu and press 1,2,3 (or the start button in midas)
* you can print the data rate of the FEB by pressing "r" in the reset menu ("q" will exit the printing)

# MIDAS Readout with the A10 Board #

* First we test the MIDAS readout with a generator from the A10 Board so make sure that you have followed all the steps for the A10 Board
* Navigate to the build directory
* `source set_env.sh`
* `cd -`
* `source start_daq.sh`
* Now a lot of Midas Frontends are starting. You should be able to see them now under localhost:8080
![4.png-1.png](https://bitbucket.org/repo/7zKBgbq/images/3540679211-4.png-1.png)
* Open a new Terminal and navigate to the build directory and again `source set_env.sh` followed by `cd -` now you can run `farm_fe`
* Open a new Terminal and navigate to the build directory and again `source set_env.sh` followed by `cd -` start the analyzer with `modules/analyzer/analyzer/analyzer_mu3e -R8088`. Now a THttpServer should be started at `localhost:8088`
* In the MIDAS GUI you should be able to run `Start Run` now and than events should show up
* If you want to use the datagenerator you can set this up in the ODB. A quick start with datagenerator can is given here:

![ezgif.com-optimize(1).gif](https://bitbucket.org/repo/7zKBgbq/images/2278595132-ezgif.com-optimize%281%29.gif)

# Simple Readout of Detector Data #

* Follow the steps for stetting up the FEB and the A10 board
* `./farm_pc/tools/swb_dmatest 0 0 0` -> when to program enters the write file state you can kill it with `ctrl+c`
* Check the output of `head memory_content.txt` should be different from 0x0 for the data
* If all of this works you can check the file if the detector data is correct

# Known Problems #
* Open Suse 15.1 with Kernel Version 4.12.14-lp151.28.91 the kernel headers (vanilla headers) can be somehow patched in comparison to the normal Linux headers. The dmabuf could fail for this headers. A fix here is to change the code in dmabuf.h.
![24B7C6E0-11E9-49AF-A6B5-C15966A9645E.jpeg](https://bitbucket.org/repo/7zKBgbq/images/3174512381-24B7C6E0-11E9-49AF-A6B5-C15966A9645E.jpeg)
* OpenSSL for Mac you need to install it via `brew install openssl` and than set the flags in your `.bash_profile`: 
```
# Open SSL
export LDFLAGS="-L/usr/local/opt/openssl@YOUR_VERSION/lib"
export CPPFLAGS="-I/usr/local/opt/openssl@YOUR_VERSION/include"
export PKG_CONFIG_PATH="/usr/local/opt/openssl@YOUR_VERSION/lib/pkgconfig"
export PATH="/usr/local/opt/openssl@YOUR_VERSION/bin:$PATH"
export LIBRARY_PATH=$LIBRARY_PATH:/usr/local/opt/openssl/lib/
```
* ROOT for Mac: use root 6.22/08 from [homebrew](https://brew.sh/index_de)
* TRB3Decoder.hxx checks if you are on Mac but this check fails Error is something like: ![63B82F73-7370-404F-88F3-4E3716AFA672.png](https://bitbucket.org/repo/7zKBgbq/images/776263305-63B82F73-7370-404F-88F3-4E3716AFA672.png)
Open the file and change the line to:
```
//#if defined(OS_LINUX) && !defined(OS_DARWIN)
//	fData[i] = __bswap_32 (fData[i]);
//#else
        fData[i] = R__bswap_constant_32(fData[i]);
//#endif
```
