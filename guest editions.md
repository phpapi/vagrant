# You need to install guest editions.

"The VirtualBox Guest Additions for all supported guest operating systems are provided as a single CD-ROM image file which is called VBoxGuestAdditions.iso. This image file is located in the installation directory of VirtualBox."
create mount directory
sudo mkdir -p /media/VirtualBoxGuestAdditions

mount guest additions iso
sudo mount -t iso9660 -o loop /installation/directory/of/VirtualBox/VBoxGuestAdditions.iso /media/VirtualBoxGuestAdditions/

Install guest additions
sudo /media/VirtualBoxGuestAdditions/VBoxLinuxAdditions.run

Then mount.vboxsf file should be in sbin and you can mount with
sudo mount -t vboxsf shared ~/host 