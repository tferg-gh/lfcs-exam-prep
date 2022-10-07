#### xfs

```sh
sudo mkfs.xfs /dev/sdb1 # format a parition as xfs
```

```sh
sudo mkfs.xfs -L "BackupVolume" /dev/sdb1 # label a volume
```

```sh
sudo xfs_admin -L "NewVolume" /dev/sdb1 # change a volumes label
```

```sh
sudo mkfs.xfs -i size=512 /dev/sdb1 # set inode size to 512 bytes
```

###### ext4

```sh
sudo mkfs.ext4 /dev/sda1 # format a partition as ext4
```

```sh
sudo mkfs.ext4 -L "BackupVolume" /dev/sda1 # label a volume
```

```sh
sudo mkfs.ext4 -N 500000 /dev/sda1 # set number of inodes
```

```sh
sudo tune2fs -l /dev/sda1 # list the properties of the file system
```

```sh
sudo tune2fs -L "OldBackupVolume" /dev/sda1 # change a label
```