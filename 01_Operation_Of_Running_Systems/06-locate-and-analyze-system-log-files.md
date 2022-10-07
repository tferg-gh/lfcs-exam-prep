**rsyslog**: Rocket-fast System Log. Logging daemon. Collects, organizes and stores logs. Stores logs in the /var/log/ directory. #var-log #rsyslog

**su & sudo --login**: Used to login as the root user #sudo-login
``` sh
su # prompt for root user password

sudo --login # prompt for password of current user with admin permissions.
```

**tail**: Shows the last few lines of a file. Using the -F command we can monitor logs in real time to see what changes are made. 
```sh
tail -F /var/log/messages
```

**which**: Displays the path to the binary for the command. #which
```sh
which sudo
/bin/sudo
```

**journalctl**: Journal Control. Manages logs a bit differently from #rsyslog. 
```sh
journalctl /bin/sudo # will show us the logs created by this binary

journalctl -u sshd.service # will show us the logs created by this unit

journalctl -e # will go to the end of the logs

journalctl -f # follow mode, show sthe last few lines of the logs as they happen
```

**-p**: To view logs based on priority we use: 
``` sh
journalctl -p err # or alert, crit, debug, merge, err, info, notice and warning
```
If you do journalctl -p **tab tab** it will display a list of priority names you can use.

**-g**: filter logs based on grep expressions using:
```sh
journalctl -p info -g '^b' # will show info logs beginning with b
```

**-S**: Display logs after a cetain time
```sh
journalctl -S 02:00 # display logs since 2am
```

**-U**: Display logs until a certain time
```sh
journalctl -S 02:00 -U 07:00 # since 2am until 7am
```

**-b**: Since last boot
```sh
journalctl -b 0 # since last boot. Use -1 for previous boot. 
```

By default, journalctl doesn't store logs for previous boots. If you want it to, make a directory here: **/var/log/journal/**

Also, most logs aren't accessible to users. You need to be **sudo** or a memeber of the **ADM** or **wheel** groups. 

**last**: View a list of users who logged into the system
```sh
tom@ubuntu:~$ last
tom      :0           :0               Thu Jun 23 07:09   still logged in
reboot   system boot  5.13.0-51-generi Thu Jun 23 07:09   still running
tom      :0           :0               Wed Jun 22 11:08 - down   (10:11)
tom      :0           :0               Wed Jun 22 09:32 - 11:08  (01:35)
```

**lastlog**: View list of each user and the last time they logged in
```sh
tom@ubuntu:~$ lastlog
Username         Port     From             Latest
root                                       **Never logged in**
daemon                                     **Never logged in**
bin                                        **Never logged in**
..
```

If the user has logged in via SSH you can see the IP address from which they logged in. 