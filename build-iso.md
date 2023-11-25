# Build ISO with the generated kernel

### Prerequisite

1- An already installed ubuntu Jammy 22 LTS \
2- The generated deb files from building the jammy folder \

### Generate ISO file
1- install the generated kernel from deb files ``sudo dpkg -i linux*4.8.0-17.19*.deb``\
2- system reboot ``sudo reboot``\
3- generate ISO file ``mkisofs -o no-image-ubuntu22.iso ~``\
4- Enjoy!