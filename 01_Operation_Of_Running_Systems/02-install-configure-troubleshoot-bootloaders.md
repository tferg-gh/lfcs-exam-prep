**Boot loader**: Starts the Linux kernel. #boot-loader

**GRUB**: Most popular #boot-loader. Stands for Grand Unified Boot Loader. #grub

**Rescue Disk**: Most Linux distributions allow you to launch a rescue disk option instead of installing the operating system. #rescue-disk

The installation will load into a rescue environment and attempt to locate and mount your existing linux installtion under /mnt/sysroot

Once the system is mounted you will need to enter the shell (usually enter). Then change the root directory using:

**chroot**: Change the root directory #chroot
``` sh
chroot /mnt/sysroot # or wherever it's been mounted to
```

**grub2-mkconfig**: Generate a GRUB config file. #BIOS #grub-mkconfig
```sh
grub2-mkconfig -o /boot/grub2/grub.cfg # -o = output
```

**grub2-mkconfig**: Generate a GRUB config file. #UEFI #grub-mkconfig
```sh
grub2-mkconfig -o /boot/efi/EFI/centos/grub.cfg # -o = output
```

**lsblk**: List block devices #lsblk 
``` sh
nvme0n1     259:0    0 232.9G  0 disk 
├─nvme0n1p1 259:1    0   512M  0 part /boot/efi
└─nvme0n1p2 259:2    0 232.4G  0 part /
```

**grub2-install**: Install the grub bootloader into the correct block device #grub-install #BIOS 
``` sh
grub2-install /dev/nvme0n1 # dev = device
```

**grub-install**: Install the grub bootloader #grub-install #UEFI
``` sh 
dnf reinstall grub2-efi grub2-efi-modules shim # dnf is the CentOS package manager
```

**/etc/default/grub**: Default configuration file for grub2. #grub-config #sudo 
```
sudo vim /etc/default/grub
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
Note: this is the file used by #grub-mkconfig to generate the config file, not the actual config file.

