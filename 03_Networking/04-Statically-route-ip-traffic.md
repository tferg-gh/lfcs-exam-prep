###### Add a static route
```sh
sudo ip route add 192.168.0.0/24 via 10.0.0.100 # traffic to network 192.168.0.0/24 sends to 10.0.0.100 

sudo ip route add 192.168.0.0/24 via 10.0.0.10 dev enp0s3 # you should also add the device name the traffic should be routed through
```

###### Remove a static route
```sh
sudo ip route del 192.168.0.0/24
```

###### Add a default route 
```sh
sudo ip route add default via 10.0.0.100 # gateway
```

These changes are temporary and will be lost on reboot. To make them permanent, use:

```sh
# Add
sudo nmcli connection modify enp0s3 +ipv4.routes "192.168.0.0/24 10.0.0.100"

# Remove
sudo nmcli connection modify enp0s3 -ipv4.routes "192.168.0.0/24 10.0.0.100"
```

What you're saying here is: If you want to reach the network at 192.168.0.0/24 route all traffic through the device at 10.0.0.100.

These settings won't be applied until the connection has been restarted. You can do that with a reboot or by using:

```sh
sudo nmcli device reapply enp0s3
```

