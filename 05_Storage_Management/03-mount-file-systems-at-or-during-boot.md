###### Temporarily mount a file system

```sh
ls /mnt/ # place to temporarily mount volumes
```

```sh
sudo mount /dev/vdb1 /mnt/ # mount a volume temporarily
```

```sh
sudo touch /mnt/testfile # create a file in the mounted volume
```

```sh
sudo umount /mnt/
```

###### Mount a filesystem at bootup
```sh
sudo vim /etc/fstab # edit to add a filesystem to mount at boot
```

``` sh
[dev_location] [mnt_point] [fs_type] [mnt_options] [dump_backup] [error_scan]

[dev_location] # /dev/sda1

[mnt_point] # /mnt

[fs_type] # xfs

[mnt_options] # default (this is usually fine to leave as default)

[dump_backup] # 0 whether the fs should be backed up by the dump utility

[error_scan] # 0 don't scan, 1 scan first (root), 2 scan after first (other)

/dev/mapper/cs-root  /  xfs  defaults  0 0
```

```sh
sudo systemctl daemon-reload # after making changes to /etc/fstab
```

##### Mount a swap file at bootup
```sh
sudo vim /etc/fstab 
```

```sh
/dev/sda1 none swap defaults 0 0 
```

###### UUIDs 
```sh
UUID=[uuid] /boot xfs defaults 0 0 
```

Devices are assigned in the order they're plugged in to the motherboard. So /dev/sda and /dev/sdb can be swapped if the devices are plugged into the other ports. To prevent this with things like the boot partition, use the UUID instead. 

```sh 
sudo blkid /dev/sda1 # show block id of partition
```