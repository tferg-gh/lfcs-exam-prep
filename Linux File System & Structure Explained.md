https://www.youtube.com/watch?v=HbgzrKJvDRw

FHS: Filesystem Heirarchy Standard. Defines the structure and layout and is maintained by the Linux Foundation.

*Note: Not all distributions follow this*

`/bin` - Binaries. This where the executable applications are typically installed. 

`/sbin` - System Binaries. Used by system administrators and typically regular users would not have access to these.

*Contains files that need to be accessible in single user mode. Single user mode logs you in as the root user and is used for performing system repairs, upgrades or testing. Networking is often disabled in this mode for security reasons.* 

*Note: When you install an application in Linux, it is not typically stored in these folders.*

`/boot` - Contains everything your OS needs to boot. Bootloaders live here.

`/cdrom` - Legacy mounting point for CD-ROM drives. Not in all distibutions will have this.

`/dev` - This is where your devices live. Typically an area where applications and drivers will access. Rarely something a user should access.

*Everything in Linux is a file. This is based on a standard used in Unix, which Linux is based off.* 

`/etc` - Et-see, edit-to-configure, confirmed by Dennis Richie to mean Etcetera. This folder stores all of your system-wide application configurations. 

*Note: User configuration and preferences are stored in the `/home` folder for the user in hidden folders either `.local`, `.config` or the application specific folder.*

`lib, lib32 & lib64` - These are where the libraries are stored. Libraries are files appliactions can use to peform various functions. Requried by binaries in `/bin` and `/sbin`.

`/media & /mnt` - These directories are where you would find your other mounted drives. Typically additional storage devices such as other hard drives, USB drives, floppy disks and network drives. 

*Note: Media was not always around, rather `/mnt` was the default. `/media` is relatively new.* 

Typically you want to use `/mnt` for manually mounted devices and the `/media` directory for OS managed devices.

`/opt`- Optional. Usually where manually installed software from vendors resides. Also where you should typically store software you've written yourself. 

`/proc` - Contains pseudo-files that contain information about running processes. Each folder in the directory correlates to a process that is running on the machine. Similar to `/dev` the files in here aren't actually files. 

`/root` - The root users home folder. It does not contain the typical users directories like Documents and Videos. Requries root permissions to access.

`/run` - A tempfs filesystem which means it runs in RAM. Everything in this directory is gone when the system is rebooted or shutdown. Used by applications that start early in the boot procedure to store runtime information that they use to function. 

`/snap` - This is a folder where snap packages are stored. Snap packages are self contained applications that run differently than normal. 

`/srv` - This is the Service directory where service data is stored. Typically empty but if you're running a web server or ftp server, you would store files accessed by users here. 

`/sys` - It is a way to interact with the kernel. Similar to the `/run` directory it is a tempfs and nothing in it is written to the disk. 

`/tmp` - This is a temporary directory. This is where applications typically store temporary files during a session. For example, if you're writing a document, it may save a copy periodically here as you're editing it. Typically emptied on a reboot. 

`/usr` - This is the user application space where applications are installed that are used by the user as opposed to the `/bin` & `/sbin` directories that are used by the system. Also known as the **unix system resource**. Applications here are typically non-essential. 

`/usr/local` - Most applications installed from source code will end up in here with binaries located at `/usr/local/bin` or `/usr/local/sbin` 

`/usr/share` - Many larger applications will install themselves here. 

*Note: Not all applications will adhere to these standards. Each developer can do whatever they want.*

`/var` - This is the variable directory. It contains files and directories that are expected to grow in size. 

`/var/crash` - Contains files about processes that have crashed.

`/var/log` - Contains system logs 

`/home` - This contains user data, such as personal files and documents. It also contains user configuration settings specific to each user. 

Hidden files will have a period infront of them and by default will not be visible unless you show hidden files with either **ctrl + h** or using a command like `ls -a`.

`/home/user/.cache` - Typically used by applications to store cached files. 

`/home/user/.local` & `/home/user/.config` - These typically store individual application settings. 

Although some applications will store their settings in their own hidden folders in the users home directory. 