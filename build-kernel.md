# generate ISO

### Add necessary dependencies

```console
sudo apt-get build-dep linux linux-image-unsigned-$(uname -r)

sudo apt-get install libncurses-dev gawk flex bison openssl libssl-dev dkms libelf-dev libudev-dev libpci-dev libiberty-dev autoconf llvm

```
### Configure the kernel
1- Enter jammy folder \
2- run ``make clean`` \
3- then ``make menuconfig`` \
4- remove multimedia support that you can find under (device drivers) > (multimedia)

### Building the kernel the old way

```console
    make clean
    make -j `getconf _NPROCESSORS_ONLN` bindeb-pkg LOCALVERSION=-custom
```
Some files will be created

```console
cd ..
ls *.deb
    linux-buildinfo-5.15.0-52-generic_5.15.0-52.58_amd64.deb
    linux-cloud-tools-5.15.0-52_5.15.0-52.58_amd64.deb
    linux-tools-5.15.0-52-generic_5.15.0-52.58_amd64.deb
```

### Testing the new kernel

Install the three-package set (on your build system, or on a different target system) with dpkg -i and then reboot:
```console
    sudo dpkg -i linux*.deb
    sudo reboot
```