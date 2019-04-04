![image](https://user-images.githubusercontent.com/34389545/35821974-62e0e25c-0a70-11e8-87dd-2cfffeb6ed47.png)

#### Master Build Status
[![Build Status](https://travis-ci.com/plenteum/plenteum-crypto.svg?branch=master)](https://travis-ci.com/plenteum/plenteum-crypto) [![Build status](https://ci.appveyor.com/api/projects/status/github/plenteum/plenteum-crypto?branch=master&svg=true)](https://ci.appveyor.com/project/plenteum/plenteum-crypto)

# Plenteum: Standalone Cryptography Library

This repository contains the necessary files to compile the cryptography library used within [Plenteum](https://www.plenteum.com) as a standalone static library that can be included in various other projects.

### How To Compile

#### Linux

##### Prerequisites

You will need the following packages: cmake (2.8 or higher), make, and git.

You will also need either GCC/G++, or Clang.

If you are using GCC, you will need GCC-7.0 or higher.

If you are using Clang, you will need Clang 6.0 or higher. You will also need libstdc++\-6.0 or higher.

##### Ubuntu, using GCC

```bash
sudo add-apt-repository ppa:ubuntu-toolchain-r/test -y
sudo apt-get update
sudo apt-get install aptitude -y
sudo aptitude install -y build-essential g++-8 gcc-8 git cmake
export CC=gcc-8
export CXX=g++-8
git clone -b master --single-branch https://github.com/plenteum/plenteum-crypto
cd plenteum-crypto
mkdir build
cd build
cmake ..
make -j
```

The static library will be built as `libplenteum-crypto.a` in the build folder.

##### Ubuntu, using Clang

```bash
sudo add-apt-repository ppa:ubuntu-toolchain-r/test -y
wget -O - https://apt.llvm.org/llvm-snapshot.gpg.key | sudo apt-key add -
```

You need to modify the below command for your version of ubuntu - see https://apt.llvm.org/

* Ubuntu 14.04 (Trusty)
- `sudo add-apt-repository "deb https://apt.llvm.org/trusty/ llvm-toolchain-trusty 6.0 main"`

* Ubuntu 16.04 (Xenial)
- `sudo add-apt-repository "deb https://apt.llvm.org/xenial/ llvm-toolchain-xenial 6.0 main"`

* Ubuntu 18.04 (Bionic)
- `sudo add-apt-repository "deb https://apt.llvm.org/bionic/ llvm-toolchain-bionic 6.0 main"`

```bash
sudo apt-get update
sudo apt-get install aptitude -y
sudo aptitude install -y -o Aptitude::ProblemResolver::SolutionCost='100*canceled-actions,200*removals'
sudo aptitude install build-essential clang-6.0 libstdc++-7-dev git cmake
export CC=clang-6.0
export CXX=clang++-6.0
git clone -b master --single-branch https://github.com/plenteum/plenteum-crypto
cd plenteum-crypto
mkdir build
cd build
cmake ..
make -j
```

The static library will be built as `libplenteum-crypto.a` in the build folder.

##### Generic Linux

Ensure you have the dependencies listed above.

If you want to use clang, ensure you set the environment variables `CC` and `CXX`.
See the ubuntu instructions for an example.

```bash
git clone -b master --single-branch https://github.com/plenteum/plenteum-crypto
cd plenteum-crypto
mkdir build
cd build
cmake ..
make -j
```

The static library will be built as `libplenteum-crypto.a` in the build folder.

#### OSX/Apple, using GCC

##### Prerequisites

- Install XCode and Developer Tools.

##### Building

```bash
which brew || /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew install --force cmake boost llvm gcc@8
export CC=gcc-8
export CXX=g++-8
git clone -b master --single-branch https://github.com/plenteum/plenteum-crypto
cd plenteum-crypto
mkdir build
cd build
cmake ..
make
```

The static library will be built as `libplenteum-crypto.a` in the build folder

#### OSX/Apple, using Clang

##### Prerequisites

- Install XCode and Developer Tools.

##### Building

```bash
which brew || /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew install --force cmake boost llvm
export CC=/usr/local/opt/llvm/bin/clang
export CXX=/usr/local/opt/llvm/bin/clang++
git clone -b master --single-branch https://github.com/plenteum/plenteum-crypto
cd plenteum-crypto
mkdir build
cd build
cmake ..
make
```

The static library will be built as `libplenteum-crypto.a` in the build folder

#### Windows

##### Prerequisites

- Install [Visual Studio 2017 Community Edition](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&page=inlineinstall)
- When installing Visual Studio, it is **required** that you install **Desktop development with C++**

##### Building

- From the start menu, open 'x64 Native Tools Command Prompt for vs2017'.
```
cd <your_plenteum-crypto_directory>
mkdir build
cd build
set PATH="C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\CommonExtensions\Microsoft\CMake\CMake\bin";%PATH%
cmake -G "Visual Studio 15 2017 Win64" ..
```

If you have errors on this step about not being able to find the following static libraries, you may need to update your cmake. Open 'Visual Studio Installer' and click 'Update'.

`MSBuild plenteum-crypto.sln /p:Configuration=Release /m`

The static library will be built as `libplenteum-crypto.lib` in the `build/Release` folder

#### AARCH64/ARM64

The following images are known to work. Your operation system image **MUST** be 64 bit.

##### Known working images

- https://github.com/Crazyhead90/pi64/releases
- https://fedoraproject.org/wiki/Architectures/ARM/Raspberry_Pi#aarch64_supported_images_for_Raspberry_Pi_3
- https://archlinuxarm.org/platforms/armv8/broadcom/raspberry-pi-3

Once you have a 64 bit image installed, setup proceeds the same as any Linux distribution. Ensure you have at least 2GB of ram, or the build is likely to fail. You may need to setup swap space.

##### Building

```bash
git clone -b master --single-branch https://github.com/plenteum/plenteum-crypto
cd plenteum-crypto
mkdir build
cd build
cmake ..
make
```

The static library will be built as `libplenteum-crypto.a` in the build folder

#### Thanks
Cryptonote Developers, Bytecoin Developers, Monero Developers, Forknote Project, TurtleCoin Community, Plenteum Developers

### Copypasta for license when editing files

Hi Plenteum contributor, thanks for forking and sending back Pull Requests. Extensive docs about contributing are in the works or elsewhere. For now this is the bit we need to get into all the files we touch. Please add it to the top of the files.

```
// Copyright (c) 2012-2017, The CryptoNote developers, The Bytecoin developers
// Copyright (c) 2014-2018, The Monero Project
// Copyright (c) 2018-2019, The TurtleCoin Developers
// Copyright (c) 2018-2019, The Plenteum Developers
//
// Please see the included LICENSE file for more information.
```
