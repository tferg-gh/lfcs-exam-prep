## SELinux
Allows fine-grained control over what users can and cannot do. 

###### SELinux Context Label Explained #selinux-context-label 
User | Role | Type | Level
-- | -- | -- | --
unconfined_u | object_r | user_home_t | s0 

###### Check if SELinux is Enabled #getenforce
```sh
getenforce
Enforcing # Enabled
Permissive # Allowing everything and logging actions
Disabled # Not enforcing security or logging actions
```

###### Set SELinux Enforcement #setenforce
```sh
sudo setenforce Enforcing # or 1
OR
sudo setenforce Permissive # or 0
```
Not case sensitive

###### List SELinux file and directory labels #ls-Z 
```sh
[vagrant@centos7 ~]$ ls -Z
drwxrwxr-x. vagrant vagrant unconfined_u:object_r:user_home_t:s0 Downloads
```
These are referred to as the #selinux-context-label aka #selinux-context or #selinux-label

###### List SELinux process lables #ps-axZ
```sh
[vagrant@centos7 ~]$ ps axZ
LABEL                             PID TTY      STAT   TIME COMMAND
system_u:system_r:init_t:s0         1 ?        Ss     0:00 /usr/lib/systemd/syst
system_u:system_r:kernel_t:s0       2 ?        S      0:00 [kthreadd]
system_u:system_r:kernel_t:s0       3 ?        S      0:00 [kworker/0:0]
system_u:system_r:kernel_t:s0       4 ?        S<     0:00 [kworker/0:0H]
system_u:system_r:kernel_t:s0       5 ?        S      0:00 [kworker/u4:0]
..
```

###### List SELinux User lables #id-Z
```sh
[vagrant@centos7 ~]$ id -Z
unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
```

###### List SELinux User Mapping #semanage-login-l
```sh
sudo semanage login -l
```

###### List SELinux User Roles #semanage-user-l
```sh
sudo semanage user -l
```
###### Update SELinux Context for a file or directory #chcon-t
```sh 
sudo chcon -t httpd_sys_content_t /var/index.html
# -u, --user=USER
# -r, --role=ROLE
# -t, --type=TYPE
# -l, --range=RANGE
```