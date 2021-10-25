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
mkdir -p ~/compiled_software
cd ~/compiled_software
git clone https://github.com/akozlins/dotfiles.git
cp dotfiles/dev/Makefile Makefile
make root
make geant4

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