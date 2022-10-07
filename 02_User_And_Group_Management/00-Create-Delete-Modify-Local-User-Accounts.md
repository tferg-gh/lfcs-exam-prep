# Local User Accounts

## List
###### List accounts #passwd 
```sh
cat /etc/passwd # all account details
```
###### List files and directories with uid #ls-ln
```sh 
ls -ln /home/ # -n = Numeric
```

###### List current user id and group id #id 
```sh
[vagrant@centos7 ~]$ id
uid=1000(vagrant) gid=1000(vagrant) groups=1000(vagrant) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c102
```
###### List current username #whoami
```sh
[vagrant@centos7 ~]$ whoami
vagrant
```
###### List new user default actions #useradd-defaults
```sh 
[vagrant@centos7 ~]$ useradd --defaults # or -D
GROUP=100
HOME=/home
INACTIVE=-1
EXPIRE=
SHELL=/bin/bash
SKEL=/etc/skel
CREATE_MAIL_SPOOL=yes
```

Other defaults for account creation are stored here: **/etc/login.defs**


###### List when a users password expires #chage-list
```sh
sudo chage --list jane
```
## Create
###### Create a user #useradd
```sh
sudo useradd john # john can be replaced with any user name
```
This will do the following: 
- Create the user **john**
- Create the group **john** and add the user **john** to it
- Create a home directory for john at **/home/john**
- Set the default shell to **/bin/bash**
- All the files from **/etc/skel** will be copied to the users home directory
- Note the account will also **not expire**


###### Create a system user #useradd-system
``` sh
sudo useradd --system sysacc # used by programs
```
This will **not** create a **home directory
###### Create a user with custom shell #useadd-shell
```sh
sudo useradd --shell /bin/othershell john # -s
```

###### Create a user with a custom home directory #useradd-home-dir
```sh
sudo useradd --home-dir /home/otherdir john # -d
```

###### Create a user with a custom uid #useradd-uid
```sh
sudo useradd -uid 1100 smith # -u 
```

###### Create a password for a user #passwd
```sh
sudo passwd john # john can be replaced with any user
```
## Delete
###### Delete a user account #userdel
```sh
sudo userdel john # use --remove before john to delete the home directory as well
```

## Modify
###### Modify user home directory #usermod-home
```sh
sudo usermod --home /home/otherdirectory --move-home john
```

###### Modify user name #usermod-login
```sh
sudo usermod --login [new_username] [old_username] 
```

###### Modify user shell #usermod-shell
```sh
sudo usermod --shell /bin/othershell jane
```

###### Disable a user #usermod-lock 
```sh
sudo usermod --lock jane
```
Note: This will only lock the users password. Using SSH keys, the user can still login. #ssh

###### Enable a user #usermod-unlock
```sh
sudo usermod --unlock jane
```

###### Set an expiration date for a user #usermod-expiredate 
```sh
sudo usermod --expiredate 2022-12-31 jane # YYYY-MM-DD
```

###### Remove an expiration date for a user #usermod-expiredate 
```sh
sudo usermod --expiredate "" jane 
```

###### Set a users password to expired #chage-lastday
```sh
sudo chage --lastday 0 jane # password is immediately expired
```

###### Set a users password to unexpired #chage-lastday
```sh
sudo chage --lastday -1 jane # unexpires the password
```

###### Set a users password to expire in 30 days #chage-maxday
```sh
sudo chage --maxday 30 jane # after 30 days jane will have to set a new password
```

###### Set a users password to never expire #chage-maxdays
```sh
sudo chage --maxday -1 jane # janes password never expires
```

