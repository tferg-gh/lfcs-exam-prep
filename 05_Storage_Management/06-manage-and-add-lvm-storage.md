###### lvm
Logical Volume Manager. Useful for using multiple disks as a single disk and expanding storage.

**install**
```sh
sudo dnf install lvm2
```

**PV, VG, LV, PE**

**PV**
Physical Volume. Real storage devices that an LVM will work with. Often an entire hard drive or solid state drive, but can also refer to a partition. 

```sh
sudo lvmdiskscan 
```

Lists what disks and partitions are available and what is already part of an LVM structure.

```sh
sudo pvcreate /dev/sdc /dev/sdd # can create multiple PVs
```

Creates a physical volume

```sh
sudo pvs
```

See what physical volumes are attached to LMV. Psize = total size and PFree = free space

```sh
sudo pvremove /dev/sde
```

Remove the PV from the LVM.

**VG**
Volume Group. A virtual disk inside LVM.

```sh
sudo vgcreate my_volume /dev/sdc /dev/sdd # can add multiple volumes to a VG
```

Create the volume group and adds the specified PVs.

```sh
sudo vgextend my_volume /dev/sde 
```

Extends the existing volume group with the PV specified.

```sh
sudo vgs
```

List volume groups.

```sh
sudo vgreduce my_volume /dev/sde
```

Remove a PV from a VG.

**LV**
Logical Volume. Like a partition for an LVM. 

```sh
sudo lvcreate --size 2G --name partition1 my_volume
```

Create a logical volume with a size of 2 Gigabytes and the name partition1 in the my_volume VG

```sh
sudo lvs
```

List LVs.

```sh
sudo lvresize --extents 100%VG my_volume/partition1
```

Extend the LV to take up the remaining space available in the VG.

```sh
sudo lvresize --size 2G my_volume/partition1 
```

Resize the LV to 2G. Note this will prompt for confirmation as it can destroy data.

```sh
sudo lvdisplay 
```

Display information about the LVs such as their paths and UUIDs. 

```sh
/dev/my_volume/partition1 # /dev/VG/LV
```

To use the the LV you'll need to create a filesystem on it

```sh
sudo mkfs.xfs /dev/my_volume/partition1
```

This will make an xfs file system on the LV

```sh
sudo lvresize --resizefs --size 3G my_volume/partition1 
```

Will resize both the LV and the fs. Otherwise it will only do the LV and you won't have any additional space in the fs. Note: Not all fs will allow you to do this, some will only allow you to grow the fs, not shrink. 

**PE**
Physical Extent. How LVM stores data across multiple disks. 