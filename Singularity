BootStrap: yum
OSVersion: 7
MirrorURL: http://mirror.centos.org/centos-%{OSVERSION}/%{OSVERSION}/os/$basearch/
Include: yum
%setup

%files

%environment
PATH="/opt/sw/python/bin:$PATH:/usr/lib64/openmpi/bin/"
LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/lib64/openmpi/lib/"
MPI_ROOT=/usr/lib64/openmpi/
export PATH
export LD_LIBRARY_PATH
export MPI_ROOT
export BOOST_ROOT=/usr/local/

%runscript

%post
    # commands to be executed inside container during bootstrap
    # add python and install some packages
    yum -y update
    yum -y install epel-release \
      centos-release-scl
    yum -y install vte-devel \
      vte291-devel \
      vte-profile \
      devtoolset-8-gcc*
    yum -y groups install "Development Tools"
    yum -y groups install "Base"
    yum -y install git cmake gcc-c++ gcc binutils \
      libX11-devel libXpm-devel libXft-devel libXext-devel \
      gcc-gfortran openssl-devel pcre-devel \
      mesa-libGL-devel mesa-libGLU-devel glew-devel ftgl-devel mysql-devel \
      fftw-devel cfitsio-devel graphviz-devel \
      avahi-compat-libdns_sd-devel openldap-devel \
      libxml2-devel gsl-devel \
      cmake3 \
      hdf5-devel \
      patch \
      qt5-qtbase-devel \
      qt5-qtsvg-devel \
      gcc-g++ numpy eigen3-devel zlib-devel qt-devel libtiff-devel \
      bzip2 ca-certificates \
      glibc-devel libXext-devel libSM-devel libXrender-devel \
      mercurial subversion \
      mesa-libGLU-devel.i686 \
      mesa-libGL-devel.i686 \
      libcanberra-gtk* \
      autoconf \
      Lmod
      
    yum -y update
    
    source /opt/rh/devtoolset-8/enable
       
    mkdir -p /storage/home
    mkdir -p /storage/work
    mkdir -p /gpfs/scratch
    mkdir -p /gpfs/group
    mkdir -p /var/spool/torque
    
    # Make symlinks
    ln -s `which qmake-qt5` /usr/local/bin/qmake
    ln -s `which moc-qt5` /usr/local/bin/moc
    ln -s `which rcc-qt5` /usr/local/bin/rcc
    ln -s `which vim` /usr/local/bin/vi
    
    ldconfig -n /usr/lib64/openmpi/lib/
    
    # Install OpenMPI 4.0.1
    cd /tmp/
    wget https://download.open-mpi.org/release/open-mpi/v4.0/openmpi-4.0.1.tar.gz
    tar -xf openmpi-4.0.1.tar.gz
    cd openmpi-4.0.1
    ./configure --prefix=/usr/lib64/openmpi/bin/
    make -j 2
    make install
    cd ..
    rm -rf openmpi-4.0.1*
    
    # Install Boost 1.70.0
    cd /tmp/
    wget https://dl.bintray.com/boostorg/release/1.70.0/source/boost_1_70_0.tar.gz
    tar -xf boost_1_70_0.tar.gz
    cd boost_1_70_0
    ./bootstrap.sh #--prefix=/usr/local
    ./b2 -j 2 install
    cd ..
    rm -rf boost_1_70_0*
    
    # Install Python 2.7.16
    mkdir -p /opt/sw/python
    export PATH=/opt/sw/python/bin:$PATH
    cd /tmp/
    wget https://www.python.org/ftp/python/2.7.16/Python-2.7.16.tar.xz
    tar -xf Python-2.7.16.tar.xz   
    cd Python-2.7.16
    ./configure --prefix=/opt/sw/python
    make -j 2
    make install
    cd ..
    rm -rf ./Python-2.7.16*
    curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
    python get-pip.py
    
    # Install Python 3.7.4
    cd /tmp/
    wget https://www.python.org/ftp/python/3.7.4/Python-3.7.4.tar.xz
    tar -xf Python-3.7.4.tar.xz
    cd Python-3.7.4
    ./configure --prefix=/opt/sw/python
    make -j 2
    make install
    cd ..
    rm -rf ./Python-3.7.4*
    python3 get-pip.py
    rm get-pip.py
    
    # Install Python packages
    pip install numpy pandas scipy matplotlib scikit-learn
