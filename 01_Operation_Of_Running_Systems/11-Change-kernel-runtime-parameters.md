# Kernel Runtime Parameters
Basically just settings for the kernel. The kernel handles low level stuff like handling memory allocation and network traffic.

## Sysctl

###### List kernel runtime parameters #sysctl-a
```sh
tom@ubuntu:~$ sudo sysctl -a # -a stands for all
[sudo] password for tom: 
abi.vsyscall32 = 1
debug.exception-trace = 1
debug.kprobes-optimization = 1
dev.cdrom.autoclose = 1
dev.cdrom.autoeject = 0
dev.cdrom.check_media = 0
dev.cdrom.debug = 0
dev.cdrom.info = CD-ROM information, Id: cdrom.c 3.20 2003/12/17
dev.cdrom.info = 
dev.cdrom.info = drive name:	
dev.cdrom.info = drive speed:	
..
```

##### Make Non-persistent Changes #non-persistent-change
These are changes for this session only and do not persist after a reboot.

###### Change kernel runtime parameters #sysctl-w 
```sh
sudo sysctl -w dev.cdrom.autoclose=0 # -w stands for write
```
Make sure there is no space before or after the **=** sign. 

##### Make Persistent Changes #persistent-change
These are changes that will occur every time we boot the system 
``` sh
# Store files with kernel runtime parameters here:
/etc/sysctl.d/

# The file can be called anything but must have the .conf extension
swap-less.conf

# Make the file 
sudo touch /etc/systcl.d/swap-less.conf

# add the contents
sudo echo 'vm.swapiness=29' > /etc/systcl.d/swap-less.conf

# now when the system reboots, it will use these parameters
```

###### Update kernel runtime parameters using files #sysctl-p
```sh
sudo sysctl -p /etc/sysctl.d/swap-less.conf
```