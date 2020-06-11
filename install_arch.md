# wallpapers

1. Check UEFI system

```
ls /sys/firmware/efi/efivars
```

```
# Check if there is internet connection
ping google.com

# Connect to wifi if not
wifi-menu

# Fix timedate if messed up
timedatectl set-ntp true

# Check all block devices
lsblk

# Create new partitions on the disc
fdisk /dev/sdb
m
p
d
p
n
1

+200M (boot partition, grub menu and all other important stuff)
Y
p
n


+12G (swap space = 150% of RAM)
p
n


+25G (root partition - (just the /, where all programs will be)
n
p (pytanie o primary)


 (enter bo to jest /home directory)
p
w (write writes all the changes made above)

# Make ext4 filesystem on the disc partitions
mkfs.ext4 /dev/sdb1 (boot partition)
mkfs.ext4 /dev/sdb3 (root partition)
mkfs.ext4 /dev/sdb4 (home partition)
lsblk

# Create swap partition out of the second one
mkswap /dev/sdb2
swapon /dev/sdb2

# Mount the arch to proper partitions
mount /dev/sdb3 /mnt
mkdir /mnt/home
ls /mnt
mkdir /mnt/boot
mount /dev/sdb1 /mnt/boot
mount /dev/sdb4 /mnt/home
lsblk

pacstrap -h
pacstrap /mnt base base-devel vim linux linux-firmware

vim /etc/fstab
genfstab /mnt (look at that dir, and shows all the mounted things in the dir)
genfstab -U /mnt >> /mnt/etc/fstab
vim /mnt/etc/fstab (delete potential /dev/sdb2 (leave only none swap) that is duplicated)

arch-chroot /mnt (logs into the actualy arch linux, and make it bootable)
vim /etc/fstab
pacman -S networkmanager
systemctl enable NetworkManager

pacman -Syu base

pacman -S grub (another boot loader, a nice menu when you first load 
    linux when chosing os, it detects partitions and decides which one is which..)

lsblk
grub-install --target=i386-pc /dev/sdb (installs grub)
grub-mkconfig -o /boot/grub/grub.cfg (make config for grub)

passwd (set password for root)

vim /etc/locale.gen (list of all differnet locales find urs, and ucomment (en_US)
locale-gen (reads the file and craetes locales for them)
vim /etc/locale.conf (set lang var 'LANG=en-US.UTF-8')

ls /etc/localtime (link that file to proper timezone file)
ls /usr/share/zoneinfo (all the potential timezones)

ln -sf /user/share/zoneinfo/Poland/Warsaw /etc/localtime

vim /etc/hostname (blank file, name the computer here)

umount -R /mnt (unmounts the disk)
reboot (from the pendrive and ready to go)

# curl -LO larbs.xyz/larbs.sh
# bash larbs.sh

pacman -S xort-xinit xorg git
cd /usr/src
git clone git://git.suckless.org/dwm
git clone git://git.suckless.org/st
git clone git://git.suckless.org/dmenu

useradd -m -g users colgate
echo "exec dwm" >> ~/.xinitrc
startx
```
