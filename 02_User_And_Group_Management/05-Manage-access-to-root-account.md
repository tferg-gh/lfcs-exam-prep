###### Run a command as root #sudo
```sh
sudo ls /root/ # will run ls with permissions of root
```

###### Login as the root user #sudo-login #sudo-permission
```sh
sudo --login # or sudo -i
```

###### Logout from root user #logout
```sh
logout # just like any other user
```

###### Login to root without sudo permission #sudo-login #sudo-password
```sh
su --login # or su - or su -l
```

###### Set password for root user
```sh
sudo passwd root
```

###### Unlock password for root user
```sh
sudo passwd --unlock root # can also use --lock
```