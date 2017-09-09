```shell
ping google.com
fdisk -l
cfdisk
#select DOS
#create 2 bootable partitions 10G & 8192M (if using 8192M ram)
#create regular partition with remainder of space
mkfs.ext4 /dev/sda1
mkfs.ext4 /dev/sda3
mkswap /dev/sda2
swapon /dev/sda2
mount /dev/sda1 /mnt
mkdir /mnt/home
mount /dev/sda3 /mnt/home
pacstrap /mnt base base-devel
genfstab /mnt>> /mnt/etc/fstab
arch-chroot /mnt /bin/bash
nano /etc/locale.gen
#uncomment en_US UTF-8 UTF-8
locale-gen
nano /etc/locale.conf
#LANG=en_US.UTF-8
ln -s /usr/share/zoneinfo/EST /etc/localtime
#rm /etc/locatime if necessary
hwclock —systohc —etc
passwd
nano /etc/hostname
#add hostname and save
systemctl enable dhcpcd
pacman -S grub os-prober
grub-install /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg
exit bash
umount /mnt
#might say target is busy
exit again
reboot

adduser
adduser to sudoers file using visudo
install emacs
pacman -S virtualbox-host-modules-arch
pacman -S xfce4 xfce4-goodies
install xorg stuff
https://www.howtoforge.com/tutorial/arch-linux-installation-with-xfce-desktop/2/
https://www.reddit.com/r/archlinux/comments/69r15f/xorgserverutils_removed/
```