BootStrap: shub
From: shub://willgpaik/centos7_aci:latest

%setup

%files

%environment
  export PATH=$PATH:/opt/sw/NAMD_2.13_Source/Linux-x86_64-g++

%runscript



%post
  yum -y update
  
  mkdir -p /opt/sw/
  cd /opt/sw/
  %wget https://raw.githubusercontent.com/willgpaik/namd_aci/master/namd_install.sh
  %chmod +x namd_install.sh
  %./namd_install.sh
  
  %rm namd_install.sh
  
  BASE=$PWD

wget https://git.psu.edu/gip5038/ics_files/raw/master/NAMD_2.13_Source.tar.gz
tar -xf NAMD_2.13_Source.tar.gz

cd NAMD_2.13_Source

tar -xf charm-6.8.2.tar
cd charm-6.8.2
env MPICXX=mpicxx ./build charm++ mpi-linux-x86_64 --with-production
cd mpi-linux-x86_64/tests/charm++/megatest
make pgm

cd $BASE/NAMD_2.13_Source

wget http://www.ks.uiuc.edu/Research/namd/libraries/fftw-linux-x86_64.tar.gz
tar xzf fftw-linux-x86_64.tar.gz
mv linux-x86_64 fftw
wget http://www.ks.uiuc.edu/Research/namd/libraries/tcl8.5.9-linux-x86_64.tar.gz
wget http://www.ks.uiuc.edu/Research/namd/libraries/tcl8.5.9-linux-x86_64-threaded.tar.gz
tar xzf tcl8.5.9-linux-x86_64.tar.gz
tar xzf tcl8.5.9-linux-x86_64-threaded.tar.gz
mv tcl8.5.9-linux-x86_64 tcl
mv tcl8.5.9-linux-x86_64-threaded tcl-threaded

./config Linux-x86_64-g++ --charm-arch mpi-linux-x86_64
cd Linux-x86_64-g++
make

cd $BASE
rm NAMD_2.13_Source.tar.gz

  
