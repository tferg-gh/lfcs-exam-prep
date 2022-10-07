##### Bind
###### Install
```sh
sudo dnf install bind bind-utils
```

###### Config
```sh 
/etc/named.conf
```

###### Listen-on
```sh
listen-on port 53 { 127.0.0.1; }; 
```
This will allow connections on port 53 from local applications installed on the computer.

```sh 
listen-on port 53 { 127.0.0.1; 192.168.0.1; };
```
You can also add the IP address of your system, you can seperate IP addresses using the semi-colon. You just need to make sure there is one after each address otherwise it will break the config. 

```sh
listen-on port 53 { any; };
```
This allows connections from any IP address

###### Allow-query
```sh
allow-query { localhost; };
```
With this set, BIND will only allow local host to query the DNS database. Only applications running on the same operating system will be able to request DNS from BIND. 

```sh
allow-query { localhost; 192.168.0.0/24; }; 
```
This will allow queries to come from addresses in the 192.168.0.0/24 range. 