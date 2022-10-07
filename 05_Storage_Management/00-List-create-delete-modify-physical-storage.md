# Disk Partitions
Dividing the available space on a disk.

## List partitions
```sh
lsblk

lsblk -f # list partitions with fs info
```

## Edit partitions
```sh
sudo cfdisk /dev/sda # where sda is the device
```

### Select label type 
``` sh
gpt # use this for most all. GUID Partition tables
dos # use this for legacy. Master Boot Record or MBR
sgi
sun
```
#lsblk #fdisk #cfdisk 