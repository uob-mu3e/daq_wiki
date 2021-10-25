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
cd ~/

# install online repo
echo "Installing online repo"
git clone git@bitbucket.org:mu3e/online.git
cd online
git checkout dev
git submodule update --init --recursive
mkdir -p build
cd build
cmake ..
make -j12
make install
cd ~/

```

.bashrc

```bash
#!/bin/bash

# If not running interactively, don't do anything
[[ $- != *i* ]] && return

alias ls='ls --color=auto'
alias l='ls -la'

PS1='[\u@\h \W]\$ '

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
# CHANGE ME
export LM_LICENSE_FILE=""

# setup root
source ~/compiled_software/root/cmake-build/bin/thisroot.sh

# setup geant
for MY_GEANT4_SH in \
    "/usr/local/bin/geant4.sh" \
    "$HOME/.local/bin/geant4.sh" \
    "$HOME/.local/geant4.cern.ch/bin/geant4.sh" \
; do
    if [ -f "$MY_GEANT4_SH" ] && cd "$(dirname -- "$MY_GEANT4_SH")" ; then
        . "$(readlink -f -- "$MY_GEANT4_SH")"
        cd - > /dev/null
        break
    fi
done

unset -v MY_GEANT4_SH

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