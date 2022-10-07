**init**: Initialization system. Starts up the system, determines crash logic. Stores instructions in **units** which are text files that contain these instructions.  #init-unit-service  #init-unit-socket #init-unit-device #init-unit-timer 

**man systemd.service**: Displays configuration options for unit confiugration files. #init-unit-service

**list-units**: This will provide a list of units for services on the system #systemctl-list-units
```sh
sudo systemctl list-units --type service --all # filters for services
```

#example #systemctl-cat 
```sh 
systemctl cat sshd.service
```

``` sh
# /lib/systemd/system/ssh.service
[Unit]
Description=OpenBSD Secure Shell server
Documentation=man:sshd(8) man:sshd_config(5)
After=network.target auditd.service
ConditionPathExists=!/etc/ssh/sshd_not_to_be_run

[Service]
EnvironmentFile=-/etc/default/ssh
ExecStartPre=/usr/sbin/sshd -t
ExecStart=/usr/sbin/sshd -D $SSHD_OPTS # commands to run on startup
ExecReload=/usr/sbin/sshd -t
ExecReload=/bin/kill -HUP $MAINPID # commands to run on reload
KillMode=process
Restart=on-failure # restart the service when it crashes
RestartPreventExitStatus=255
Type=notify
RuntimeDirectory=sshd
RuntimeDirectoryMode=0755
..
```

**edit --full**: Edit the unit configuration #systemctl-edit
```sh
sudo systemctl edit --full sshd.service
```

**revert**: Undo changes to the unit configuration #systemctl-revert
``` sh
sudo systemctl revert sshd.service
```

**status**: Displays information about the service #systemctl-status 
```sh
sudo systemctl status sshd.service
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: e>
     Active: active (running) since Wed 2022-06-22 11:43:28 AEST; 5min ago
       Docs: man:sshd(8)
             man:sshd_config(5)
   Main PID: 15793 (sshd)
      Tasks: 1 (limit: 18900)
     Memory: 1.0M
     CGroup: /system.slice/ssh.service
             └─15793 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups

Jun 22 11:43:28 ubuntu systemd[1]: Starting OpenBSD Secure Shell server...
Jun 22 11:43:28 ubuntu sshd[15793]: Server listening on 0.0.0.0 port 22.
Jun 22 11:43:28 ubuntu sshd[15793]: Server listening on :: port 22.
Jun 22 11:43:28 ubuntu systemd[1]: Started OpenBSD Secure Shell server.
```

**stop**: Close the program this service unit controls. #systemctl-stop
``` sh
sudo systemctl stop sshd.service
```

**start**: Start the program the service unit controls manually. #systemctl-start
```
sudo systemctl start sshd.service
```

**restart**: Restart the program the service unit controls. Loads new settings. #systemctl-restart
``` sh
sudo systemctl restart sshd.service
```

**reload**: Restart the program the service unit controls gracefully. #systemctl-reload
```sh
sudo systemctl reload ssh.service
```

**reload-or-restart**: Tries to reload first and if it's not supported, then restat. #systemctl-reload-or-restart #systemctl-reload #systemctl-restart 
```sh
sudo systemctl reload-or-restart ssh.service
```

**disable**: Stops the program from starting at boot time. #systemctl-disable
``` sh
sudo systemctl disable ssh.service
```

**is-enabled**: Simply checks if the program is enabled. #systemctl-is-enabled
```sh
sudo systemctl is-enabled ssh.service
```

**enabled**: Starts the program at boot-up. #systemctl-enabled
```sh
sudo systemctl enable ssh.service 
```

**--now**: Can be used when #systemctl-enabled or #systemctl-disable to both #systemctl-start  or #systemctl-stop the program respectivley.
``` sh
sudo systemctl enable --now ssh.service

OR

sudo systemctl disable --now ssh.service
```

Sometimes applications we've stopped and disabled will still be running and that's often because another application has started it. We can brute force disable this by using the **mask** option. #systemctl-mask
```sh
sudo systemctl mask atd.service # cannot be enabled or started

OR 

sudo systemctl unmask atd.serice
```

