# Requirements #
* Front End Board
* [A10 Dev Board](https://www.terasic.com.tw/cgi-bin/page/archive.pl?Language=English&CategoryNo=231&No=970#https://www.terasic.com.tw/attachment/archive/970/image/DE5a-Net_45d.jpg)
* [Si5338 Clk board](https://www.silabs.com/documents/public/user-guides/Si5338-EVB.pdf)
* Root 6 with CXX > 14
* Linux Kernel > 4.12
* Quartus
* TODO: Detector stuff?

# Quartus Setup #
* A setup script for the quartus environment is located at `common/firmware/util/altera/quartus.sh` you can also place this to your `.bashrc`

# Installation Hardware #
* Programm the Clk board in such a way that it has two synchronized clk outputs (each having 125MHz). One needs to be a differential LVDS clk and the other one needs to be a CMOS output.
(TODO: upload a configuration file here, is there soldering needed for CMOS output?)
* Connect the two clks to the FPGA Boards (TODO: add picture from the lab with the connections)
* Remark: for the testing the A10 board standalone one can just connect the two SMA ports on the board (TODO: picture)
* TODO: what is missing?


# Installation Software #
* `git clone git@bitbucket.org:mu3e/online.git`
* `git checkout DEV-BRANCH`
* `git submodule update —init —-recursive`
* `mkdir build`
* `cd build`
* `cmake ..`
* `make`
* `make install`

# Compile A10 Hardware #
* A basic A10 board file is stored at https://seafile.rlp.net/d/399ebc0f7e5b49d59522/ at `Mu3e Firmware/SWB/ SWB_debug_sof_file/top_signaltap.sof`
* Download this file and navigate to `online/switching_pc/a10_board/`
* Connect the A10 board via a USB cable to you PC and execute `jtagconfig` and check if the device is showing up
* `make SOF=PATH_TO_top_signaltap.sof pgm`
* `make app_upload`
* `make terminal`
* Now the NIOS terminal of the A10 board should show up (TODO: add picture)
* Close this terminal again and navigate to `common/kerneldriver`
* `make` for compiling the kernel modules
* The following lines are only possible if the A10 was flashed with a PCIe firmware before (see Flash A10 board) and you need to redo them after you programmed the device via `make pgm`
* Since the device is reprogrammed we have to rescan the PCIe devices.
* First we need the find the device number `sudo lspci | grep Altera` -> "dev_number" Unassigned class [ff00]: Altera Corporation Device 0004 (rev 01) 
* Than we need to remove this device and rescan it.
* `sudo su` in the `common/kerneldriver` folder
* `echo 1 > /sys/bus/pci/devices/0000:"dev_number"/remove`
* `echo 1 > /sys/bus/pci/rescan`
* Now you should have two devices under `/dev/mudaq*`. One is the FPGA the other one the DMA buffer.
* Loading the FPGA driver with `./load_mudaq.sh`
* Chang the permissions of the devices so a normal user can use them `chmod go+rw /dev/mudaq*`

# Test A10 Device #
* If the A10 device showed up correctly a view tests can be performed to check wheaten the device is working
* Navigate to the build directory 
* First lets check the PCIe registers 
* `./farm_pc/tools/rw rr 0x1` -> should show a hex value != 0x0
* Now lets try to readout the DMA buffer with generated data
* `./farm_pc/tools/swb_dmatest 2 0 0` -> when to program enters the write file state you can kill it with `ctrl+c`
* Check the output of `head memory_content.txt` should be different from 0x0 for the data
* If all of this works you can continue 

# Flash A10 Board (optional and need to be done only once) #
* If the board is used the first time a factory firmware is loaded when starting the FPGA. Since the FPGA is used as a PCIe device a custom firmware need to be loaded to this flash so the device can be recognized as a PCIe device.
* Run the commands from Compile Hardware for the A10 board
* Open the flash GUI to flash the sof file (Firmware configuration) and elf file (software for the NIOS) to the A10. `./common/firmware/a10_tcl/program_gui.sh` (TODO: picture)
* Choose the sof file and elf file you want to flash to the device and execute the flashing.
* TODO: @Alex: is this correct?

# Compile FEB Hardware #
* TODO ...

# Test MIDAS with the A10 Board #
* First we test the MIDAS readout with a generator from the A10 Board so make sure that you have followed all the steps for the A10 Board
* Navigate to the build directory
* `source set_env.sh`
* `cd -`
* `source start_daq.sh`
* Now a lot of Midas Frontends are starting. You should be able to see them now under localhost:8080
 (TODO: add picture)
* Open a new Terminal and navigate to the build directory and again `source set_env.sh` followed by `cd -` now you can run `farm_fe`
* Open a new Terminal and navigate to the build directory and again `source set_env.sh` followed by `cd -` start the analyzer with `modules/analyzer/analyzer/analyzer_mu3e -R8088`. Now a THttpServer should be started at `localhost:8088`
* In the MIDAS GUI you should be able to run `Start Run` now and than events should show up

# Simple Readout of Detector Data #
* Follow the steps for stetting up the FEB and the A10 board
* `./farm_pc/tools/swb_dmatest 0 0 0` -> when to program enters the write file state you can kill it with `ctrl+c`
* Check the output of `head memory_content.txt` should be different from 0x0 for the data
* If all of this works you can check the file if the detector data is correct

# MIDAS Readout with Detector Data #