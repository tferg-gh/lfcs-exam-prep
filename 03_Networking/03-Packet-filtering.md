###### Get default zone #firewalld
``` sh
firewall-cmd --get-default-zone
```

###### Change default zone #firewalld 
```sh
firewall-cmd --set-default-zone=public
```

###### List current firewall rules #firewalld 
```sh
sudo firewall-cmd --list-all
```

###### List service port #firewalld 
```sh
sudo firewall-cmd --info-service=cockpit
```

###### Allow a service or port through the firewall #firewalld 
```sh
sudo firewall-cmd --add-service=http
OR
sudo firewall-cmd --add-port=80/tcp
```

###### Remove a service or port from the firewall #firewalld 
```sh
sudo firewall-cmd --remove-service=http
OR
sudo firewall-cmd --remove-port=80/tcp
```

###### Create a trusted zone #firewalld 
```sh 
sudo firewall-cmd --add-source=10.11.12.0/24 --zone=trusted
```

###### List active zones #firewalld 
```sh
firewall-cmd --get-active-zones
```

###### Remove a trusted zone #firewalld 
```sh
sudo firewall-cmd --remove-source=10.11.12.0/24 --zone=trusted
```

###### Make rules permanent #firewalld 
```sh 
sudo firewall-cmd --runtime-to-permanent
OR
sudo firewall-cmd --add-port=12345/tcp --permanent #doesn't implement for current session
```