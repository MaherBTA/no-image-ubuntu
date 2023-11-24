# generate ISO

### Add necessary dependencies

```console
sudo apt-get build-dep linux linux-image-unsigned-$(uname -r)

sudo apt-get install libncurses-dev gawk flex bison openssl libssl-dev dkms libelf-dev libudev-dev libpci-dev libiberty-dev autoconf llvm

```

### Building the kernel

```console
    LANG=C fakeroot debian/rules clean
    # quicker build:
    LANG=C fakeroot debian/rules binary-headers binary-generic binary-perarch
    # if you need linux-tools or lowlatency kernel, run instead:
    LANG=C fakeroot debian/rules binary
```
A three deb files will be created

```console
cd ..
ls *.deb
    linux-headers-4.8.0-17_4.8.0-17.19_all.deb
    linux-headers-4.8.0-17-generic_4.8.0-17.19_amd64.deb
    linux-image-4.8.0-17-generic_4.8.0-17.19_amd64.deb
```

### Testing the new kernel

Install the three-package set (on your build system, or on a different target system) with dpkg -i and then reboot:
```console
    sudo dpkg -i linux*4.8.0-17.19*.deb
    sudo reboot
```