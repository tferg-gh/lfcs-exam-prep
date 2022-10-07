###### List available connections
```sh
[vagrant@centos7 ~]$ nmcli connection show
NAME         UUID                                  TYPE      DEVICE
System eth0  5fb06bd0-0bb0-7ffb-45f1-d6edd65f3e03  ethernet  eth0
System eth1  9c92fad9-6ecb-3e6c-eb4d-8a47c6f50c04  ethernet  eth1
```

###### Enable auto-connect to network on boot
```sh
sudo nmcli connection modify [connection_name] autoconnect yes
```