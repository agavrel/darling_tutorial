# How to install Darling (Ubuntu 20.04)

### Install Clang version 12

First you will need to [download the binaries](https://github.com/llvm/llvm-project/releases/tag/llvmorg-12.0.0) from the official website.

Once done move them to `/usr/local`

```	
mv clang+llvm-12.0.0-x86_64-linux-gnu-ubuntu-20.04/ clang_12.0.0 && sudo mv clang_12.0.0 /usr/local
```

Add to path:
```
export PATH=/usr/local/clang_12.0.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/clang_12.0.0/lib:$LD_LIBRARY_PATH
```

### Install Darling


Now install [darling](https://docs.darlinghq.org/build-instructions.html)

#### Dependencies

```
sudo apt install cmake clang bison flex libfuse-dev libudev-dev pkg-config libc6-dev-i386 \
linux-headers-generic gcc-multilib libcairo2-dev libgl1-mesa-dev libglu1-mesa-dev libtiff5-dev \
libfreetype6-dev git libelf-dev libxml2-dev libegl1-mesa-dev libfontconfig1-dev libbsd-dev \
libxrandr-dev libxcursor-dev libgif-dev libavutil-dev libpulse-dev libavformat-dev libavcodec-dev \
libavresample-dev libdbus-1-dev libxkbfile-dev libssl-dev
```

#### Fetch the sources (need 4GB)

```
git clone --recursive https://github.com/darlinghq/darling.git
```

#### Build (About 10GB)

```
cd darling && mkdir build && cd build
cmake ..
make
sudo make install

```

You will also need the following module:
```
make lkm
sudo make lkm_install
```
