###### List listening programs #ss #netstat
```sh
sudo ss -ltunp # or tunlp
```

``` sh
-l = listening
-t = tcp
-u = udp
-n = numeric values
-p = processes # requires sudo
```

```sh
127.0.0.1 = Local host
0.0.0.0 = External Connections
[::] = IPv6 Address for 0.0.0.0
[::1] = IPv6 Address for 127.0.0.1
```