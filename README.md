### Linux

#### Install
Our library has been tested on Linux. There are several library dependencies including Boost, Miracl,Relic,NTL and Sparsehash.

#### Install gcc-8,g++-8
    sudo add-apt-repository ppa:ubuntu-toolchain-r/test
    sudo apt-get update
    sudo apt-get install gcc-8 g++-8 -y
    cd /usr/bin
    sudo rm gcc
    sudo ln -s /usr/bin/gcc-8 gcc
    sudo rm g++
    sudo ln -s /usr/bin/g++-8 g++
#### Install cmake-3.14.0
    sudo apt-get autoremove cmake
    wget https://github.com/Kitware/CMake/releases/download/v3.14.0/cmake-3.14.0.tar.gz
    tar -xzvf cmake-3.14.0.tar.gz
    cd cmake-3.14.0
    ./configure
    make
    sudo make install
    cmake -version

### Install the following library dependencies,put those library under \cryptoTools\thirdparty\linux.

#### Install boost(1.69)

    sudo apt --purge remove libboost-dev
    sudo apt --purge remove libboost-all-dev
    sudo apt --purge autoremove libboost-all-dev
    sudo rm -rf /usr/lib/libboost_*
    sudo rm -rf /usr/include/boost
    wget https://dl.bintray.com/boostorg/release/1.69.0/source/boost_1_69_0.tar.gz
    tar -xzvf boost_1_69_0.tar.gz
    mv boost_1_69_0 boost
    cd boost
    ./bootstrap.sh
    sudo ./b2 install -j4
    sudo /bin/bash -c 'echo "/usr/local/lib" > /etc/ld.so.conf.d/boost.conf'
    sudo ldconfig
    cat /usr/local/include/boost/version.hpp | grep "BOOST_LIB_VERSION"

#### Install miracl

    git clone https://github.com/ladnir/miracl
    cd miracl/miracl/source/
    sudo bash linux64

#### Install Relic

    git clone https://github.com/relic-toolkit/relic.git
    cd relic
    cmake . -DMULTI=OPENMP
    make
    sudo make install

#### Install NTL

    wget http://www.shoup.net/ntl/ntl-9.3.0.tar.gz
    tar -zxvf ntl-9.3.0.tar.gz
    mv ntl-9.3.0 ntl
    cd ntl/src
    ./configure
    make
    sudo make install

#### Install Sparsehash

    git clone https://github.com/sparsehash/sparsehash.git
    cd sparsehash
    ./configure
    make
    sudo make install

### make
Switch working directory to project root directory

    cmake . -DENABLE_MIRACL=ON
    make

### run

    ./bin/frontend_psi