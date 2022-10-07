##### quota

```sh
sudo dnf install quota
```

This will install the quota application. Note: It may already be installed. 

To add quotas to a file system, edit the `/etc/fstab` record and modify the options to include:

```sh
sudo vim /etc/fstab

/dev/vdb1 /mybackups xfs defaults,usrquota,grpquota 0 2
```

The `usrquota` and `grpquota` options are added to the configuration. After saving the file and rebooting the machine, on an XFS file system, the job is done. On ext4 you need to do extra steps. 

```sh
sudo quotacheck --create-files --user --group /dev/vdb1
```

This will create two file in the file system, `aquota.group` and `aquota.user`. These files are used to keep track of how much space each user or group is using. 

```sh
sudo quotaon /mnt/
```

You would also need to enable the quota for the mount point. 

```sh
fallocate --length 100M /mybackups/aaron/100Mfile
```

This command `fallocate` will create a file at the location as big as is specified by the `--length`option 

```sh
sudo edquota --user aaron
```

Use this to edit the Disk quotas for user aaron. 

`blocks` is how much data the user is using currently. 

`inodes` refers to the number of files the user has in the system. 

`Soft` is the soft limit you can put on data. If the user goes over this quota they'll have a grace period to free up some space or delete some files before the system imposes a hard limit and stops them from creating anymore. 

`Hard` is the hard limit and restricts the user from creating any more data above this quota. 

Note: A `0` in these fields denotes that there is no quota imposed on the user.

These values are displayed in blocks. So 102400 blocks is equal to 100M and you can set a quota using this shorthand instead of determining the total blocks. K, M, G, T, P, Z are all useable.

```sh
sudo quota -edit-period
```

This will allow you to modify the grace period for users.