##### mdadm
Multiple devices administration

```sh
sudo mdadm --create /dev/md0 --level=0 --raid-devices=3 /dev/vdc /dev/vdd /dev/vde
```

`/dev/md0` is the block device created by creating this array. This can be treated as a regular disk.

```sh
sudo mkfs.ext4 /dev/md0
```

As with a normal block device you can simply create a file system on it.

```sh
sudo mdadm --stop /dev/md0
```

Stop or deactivate the array. Note: When linux boots, it will scan the superblocks for information about any RAID arrays and attempt to rebuild them. They'll typically be assigned to something like `/dev/md127`

To remove the information from the superblocks and avoid that issue, use:

```sh
sudo mdadm --zero-superblock /dev/vdc /dev/vdd /dev/vde
```

```sh
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/vdc /dev/vdd --spare-devices=1 /dev/vde
```

This will create an array containing both block devices `/dev/vdc` and `/dev/vdd` and if one of those devices fails it will use `/dev/vde` to make up the rest of the array. 

```sh
sudo mdadm --manage /dev/md0 --add /dev/vde
```

This will add another disk to an existing array.

```sh
cat /proc/mdstat
```

This provides information regarding the status of the array. How many devices are active and how many are unused. Note: Personalities = RAID Types.

```sh
sudo mdadm --manage /dev/md0 --remove /dev/vde
```