# GNS3 Linux Installation

Ubuntu-based distributions (64-bit only) Example:

sudo apt update

sudo add-apt-repository ppa:gns3/ppa

sudo apt update

sudo apt install gns3-gui gns3-server

sudo usermod -aG ubridge,libvirt,kvm $(whoami)

sudo chmod 755 /usr/bin/ubridge

More Information:

https://docs.gns3.com/docs/getting-started/installation/linux

For Wireshark:

sudo usermod -aG ubridge,libvirt,kvm,wireshark $(whoami)
