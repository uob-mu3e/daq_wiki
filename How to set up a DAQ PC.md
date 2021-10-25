Setup script
```bash
# install midas
DIR="~/midas"
echo "Installing midas in ${DIR}..."
cd ~/
git clone git@bitbucket.org:tmidas/midas.git
cd midas
git submodule update --init --recursive
mkdir -p build
cd build
cmake ..
make -j12
make install
cd ~/

# install root / geant4
echo "Installing libs for root/geant (libuuid-devel)"
sudo zypper install libuuid-devel

mkdir -p ~/compiled_software
cd ~/compiled_software
git clone https://github.com/akozlins/dotfiles.git
cp dotfiles/dev/Makefile Makefile
make root -j12
make geant4 -j12

```

.bashrc

```bash
# setup quartus
export INTELFPGAOCLSDKROOT="~/intelFPGA/18.1/hld"
export QSYS_ROOTDIR="~/intelFPGA/18.1/quartus/sopc_builder/bin"
export ALTERAPATH="~/intelFPGA/18.1"
export ALTERAOCLSDKROOT="${ALTERAPATH}/hld"
export QUARTUS_ROOTDIR=${ALTERAPATH}/quartus
export SOPC_KIT_NIOS2=${QUARTUS_ROOTDIR}/../nios2eds
export QUARTUS_ROOTDIR_OVERRIDE="$QUARTUS_ROOTDIR"
export PATH=$PATH:${ALTERAPATH}/quartus/bin
export PATH=$PATH:${ALTERAPATH}/nios2eds/bin
export PATH=$PATH:${ALTERAPATH}/nios2eds/sdk2/bin
export PATH=$PATH:${ALTERAPATH}/nios2eds/bin/gnu/H-x86_64-pc-linux-gnu/bin
export PATH=$PATH:${QSYS_ROOTDIR}
export LM_LICENSE_FILE=1800@galileo.zdv.uni-mainz.de

source ~/compiled_software/root/bin/thisroot.sh

```



* OpenSuse 15.3
* Separate partitions for /home and os (/)
* Extra disks shall be mounted as /data1, /data2 etc.
* two users labor (uid 11001) & mu3e (uid 11000)
* Both with MIDAS installed in the home directory and login scripts setting the corresponding paths
* Both with online (stable for mu3e, development for labor) installed in the home directory and login scripts setting the corresponding paths
* cuda (if a GPU is present)
* Quartus
* geant4 use https://github.com/akozlins/dotfiles/blob/master/dev/Makefile
* root use https://github.com/akozlins/dotfiles/blob/master/dev/Makefile