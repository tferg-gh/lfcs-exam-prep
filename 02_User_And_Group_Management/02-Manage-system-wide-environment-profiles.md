###### List current users environment variables #env
```sh
vagrant@centos7 ~]$ printenv # or env
XDG_SESSION_ID=2
HOSTNAME=centos7.localdomain
SELINUX_ROLE_REQUESTED=
TERM=xterm-256color
SHELL=/bin/bash
HISTSIZE=100000
SSH_CLIENT=10.0.2.2 41624 22
SELINUX_USE_CURRENT_RANGE=
SSH_TTY=/dev/pts/0
USER=vagrant
..
```

###### Temporarily modify an existing environment variable #env #non-persistent-change #bash #current-user
```sh
HISTSIZE=200000 # VARIABLE=VALUE
```

###### Permanently modify an environment variable #env #persistent-change #bash #current-user 
``` sh
vim .bashrc # add the environment variable here

export MYVAR=TRUE

source ~/.bashrc
```

###### Permanently modify environment variables for all users #env #persistent-change #bash #all-users #etc-environment
```sh
sudo vim /etc/environment # add the environment variable here
```

###### List command history #history #bash 
``` sh
tom@ubuntu:~$ history # display a list of commands
    1  sudo apt update
    2  sudo apt upgrade
    3  mkdir .icons
    4  mkdir .themes
    5  gsettings set org.gnome.desktop.interface gtk-theme "Dracula"
    6  gsettings set org.gnome.desktop.wm.preferences theme "Dracula"
    7  gsettings set org.gnome.desktop.interface icon-theme "Dracula"
    8  sudo apt update
    9  sudo apt install vim
..
```

###### Output contents of variable #env #bash 
``` sh
echo $HOME
/home/tom
```

###### Run a script on user login 
```sh
sudo vim /etc/profile.d/ # put a script in this directory
```
Note: Does not need a shebang !#

###### Modify the files copied into a new users directory #etc-skel
``` sh
sudo vim /etc/skel/README # the /etc/skel/ directory will be copied to new users on creation
```