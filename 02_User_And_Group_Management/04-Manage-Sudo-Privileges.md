Users that are part of the wheel group can run commands as sudo. 

###### Add a user to a group #gpasswd-add 
```sh
sudo gpasswd --add trinity wheel
```

###### Remove a user from a group #gpasswd-delete 
```sh
sudo gpasswd --delete trinity wheel
```

The file responsible for which users can use sudo and what commands they can run is located here:  #etc-sudoers #visudo
```sh
tom@ubuntu:~$ sudo cat /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	mail_badpass
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

```
Note: Parentheses hints the field is optional

``` sh
[user/group] [host]=[run_as_user] [COMMANDS]
```


###### Edit the sudoers file #visudo
```sh
sudo visudo #opens in default text editor, checks syntax to avoid mistakes
```

###### Provide a user sudo permissions
```sh
trinity   ALL=(ALL:ALL)   ALL # grants all permissions to run all commands as all users to user trinity
```

###### Provide a group sudo permissions
```sh
%developers ALL=ALL # note the run as users has been ommitted users who are part of the developer group can run ALL commands from any host
```

###### Remove password requirements
```sh
trinity ALL= NOPASSWD:ALL # can run all commands without a password
```