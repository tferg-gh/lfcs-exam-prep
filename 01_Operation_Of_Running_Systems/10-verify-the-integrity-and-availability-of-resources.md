## Disk
###### List free disk space #df
``` sh
# -h is for human readable, displays size in Megabytes and Gigabytes
tom@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.7G     0  7.7G   0% /dev
tmpfs           1.6G  2.2M  1.6G   1% /run
/dev/nvme0n1p2  228G   80G  137G  37% /
tmpfs           7.8G  4.3M  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop0      134M  134M     0 100% /snap/chromium/2020
/dev/loop2      249M  249M     0 100% /snap/gnome-3-38-2004/99
/dev/loop1      128K  128K     0 100% /snap/bare/5
/dev/loop3       82M   82M     0 100% /snap/gtk-common-themes/1534
/dev/loop4      165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop5       66M   66M     0 100% /snap/gtk-common-themes/1519
/dev/loop7       56M   56M     0 100% /snap/core18/2409
/dev/loop6       62M   62M     0 100% /snap/core20/1518
/dev/loop8       62M   62M     0 100% /snap/core20/1494
/dev/loop9       74M   74M     0 100% /snap/obsidian/x1
/dev/nvme0n1p1  511M  5.3M  506M   2% /boot/efi
/dev/loop10      51M   51M     0 100% /snap/snap-store/547
/dev/loop11     219M  219M     0 100% /snap/gnome-3-34-1804/77
/dev/loop12     219M  219M     0 100% /snap/gnome-3-34-1804/72
/dev/loop13     132M  132M     0 100% /snap/chromium/2011
/dev/loop14      56M   56M     0 100% /snap/core18/2128
/dev/loop15      55M   55M     0 100% /snap/snap-store/558
/dev/loop16      47M   47M     0 100% /snap/snapd/16010
/dev/loop17     255M  255M     0 100% /snap/gnome-3-38-2004/106
/dev/loop18      45M   45M     0 100% /snap/snapd/15904
tmpfs           1.6G  1.8M  1.6G   1% /run/user/1000
```
You can ignore udev, tmpfs, tmpfs and /dev/loop*

###### List size of directory #du
```sh
# -s is for summarize, displays only this directory, not recursive
tom@ubuntu:~$ du -sh /bin/
343M	/bin/
```

###### Verify integrity of an XFS file system #xfs_repair
```sh
sudo xfs_repair -v /dev/vdb1 # -v enables verbose output
```

###### Verify integrity of an EXT4 file system #fsck-ext4
```sh
sudo fsck.ext4 -v -f -p /dev/vdb2 
# -v enables verbose
# -f forces a check even if fs reports healthy
# -p enables preen which fixes simple problems automatically
```

## RAM
###### List free memory #free
``` sh
# sizes are in Mebibytes and Gibibytes 1 Mebibyte = 2^20 = 1,048,576 bytes
tom@ubuntu:~$ free -h
              total        used        free      shared  buff/cache   available
Mem:           15Gi       6.6Gi       2.6Gi       491Mi       6.3Gi       8.0Gi
Swap:         2.0Gi       792Mi       1.2Gi
```

## CPU
###### List recent CPU Core usage #uptime
```sh
tom@ubuntu:~$ uptime  # load average: last 1min, 5min, 15min
 12:56:11 up 1 day,  5:46,  1 user,  load average: 0.74, 0.83, 0.82
```
1 = 1 CPU Core used 100% for that time. 

###### List CPU information #lscpu
```sh
tom@ubuntu:~$ lscpu
Architecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
Address sizes:                   39 bits physical, 48 bits virtual
CPU(s):                          12
On-line CPU(s) list:             0-11
Thread(s) per core:              2
Core(s) per socket:              6
Socket(s):                       1
NUMA node(s):                    1
Vendor ID:                       GenuineIntel
CPU family:                      6
Model:                           158
Model name:                      Intel(R) Core(TM) i7-8850H CPU @ 2.60GHz
Stepping:                        10
CPU MHz:                         2600.000
CPU max MHz:                     4300.0000
CPU min MHz:                     800.0000
BogoMIPS:                        5199.98
Virtualisation:                  VT-x
L1d cache:                       192 KiB
L1i cache:                       192 KiB
L2 cache:                        1.5 MiB
L3 cache:                        9 MiB
NUMA node0 CPU(s):               0-11
..
```

###### List details about other hardware #lspci
```sh
tom@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Mobile)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 07)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10)
00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
00:15.0 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #0 (rev 10)
00:15.1 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #1 (rev 10)
00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
00:17.0 SATA controller: Intel Corporation Cannon Lake Mobile PCH SATA AHCI Controller (rev 10)
00:1c.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #6 (rev f0)
00:1c.6 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #7 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #9 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device a30e (rev 10)
00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (7) I219-LM (rev 10)
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
02:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
03:00.0 Non-Volatile memory controller: Kingston Technology Company, Inc. Device 2263 (rev 03)
```

## Services 
###### List status of all services #systemctl-list-dependencies
```sh 
tom@ubuntu:~$ systemctl list-dependencies
default.target
● ├─accounts-daemon.service # green
● ├─apport.service # green
● ├─e2scrub_reap.service # white
● ├─gdm.service # green
● ├─switcheroo-control.service # green
● ├─systemd-update-utmp-runlevel.service #white
● ├─udisks2.service # green
● └─multi-user.target # green
..
```
The colors aren't displaying but green dots indicate they're running and white dots indicate they're stopped. Not all services need to be running all the time, some run once at startup and then stop. 