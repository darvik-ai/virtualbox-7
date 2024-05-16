Install VirtualBox on Ubuntu 22.04
1. Update your system’s package cache. This command refreshes the list of available packages and their versions from the repositories configured on your system:

sudo apt update
2. Import VirtualBox package repositories keys. These commands download Oracle’s public keys and add them to your system’s list of trusted keys. These keys are used to verify the integrity of the packages you download from Oracle’s repositories:

$ curl https://www.virtualbox.org/download/oracle_vbox_2016.asc | gpg --dearmor > oracle_vbox_2016.gpg
$ curl https://www.virtualbox.org/download/oracle_vbox.asc | gpg --dearmor > oracle_vbox.gpg
$ sudo install -o root -g root -m 644 oracle_vbox_2016.gpg /etc/apt/trusted.gpg.d/
$ sudo install -o root -g root -m 644 oracle_vbox.gpg /etc/apt/trusted.gpg.d/
3. Add the VirtualBox repository. This command adds Oracle’s VirtualBox repository to your system’s list of repositories.:

echo "deb [arch=amd64] http://download.virtualbox.org/virtualbox/debian $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
4. Install VirtualBox and its required dependencies with these commands:

sudo apt update
sudo apt install -y linux-headers-$(uname -r) dkms
sudo apt install virtualbox-7.0 -y
5. (Optional) For enhanced functionality such as USB 2.0 and 3.0 support, PXE boot for Intel network cards, disk encryption, and VirtualBox Remote Desktop Protocol (RDP), consider installing the VirtualBox Extension Pack. Here’s how you can download and install it:

wget https://download.virtualbox.org/virtualbox/7.0.0/Oracle_VM_VirtualBox_Extension_Pack-7.0.0.vbox-extpack
sudo VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-7.0.0.vbox-extpack
Note: Replace “7.0” with the latest version of VirtualBox when you’re installing it.
