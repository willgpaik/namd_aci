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
  wget https://raw.githubusercontent.com/willgpaik/namd_aci/master/namd_install.sh
  chmod +x namd_install.sh
  ./namd_install.sh
  
  
