###### findmnt
Shows all mount points, including virtual mounts.

```sh
findmnt
```

**list only certain filesystem types**
```sh
findmnt -t xfs,ext4 # does both xfs and ext4
```

```sh 
TARGET      SOURCE               FSTYPE      OPTIONS
/			/dev/mapper/cs-root	 xfs		 rw,relatime,seclabel,attr2,inode64...			
```

**options**
```sh
rw,relatime,seclabel,attr2,inode64,logbufs=8,logbsize=32k,noquota
```

rw = read write
ro = read only
noexec = cannot execute programs stored on this fs
nosuid = disables suid function that allows programs to run with root privelages without using the sudo command

```sh
sudo mount -o ro,noexec,nosuid /dev/vdb2 /mnt
```

**Remount a file system using new options**
```sh
sudo mount -o remount,rw /dev/vdb2 /mnt
```

Don't remount for filesystem independant options, umount, then mount. 

**Mount fs with options permanently**
```sh
sudo vim /etc/fstab

/dev/vdb2 /mnt xfs ro,noexec 0 2 # replaces default
```