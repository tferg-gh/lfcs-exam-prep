Chrony daemon is used on CentOS to keep accurate time. You can check it's status by using:
```sh
systemctl status chronyd.service
```

You could also use the command:
```sh
timedatectl
```

###### Set timezone
```sh
sudo timedatectl set-timezone America/New_York
```

###### List timezones
```sh
timedatectl list-timezones
```

###### Enable NTP service
```sh
sudo timedatectl set-ntp true
```