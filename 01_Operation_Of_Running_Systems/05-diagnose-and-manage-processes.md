**ps**: Show running processes #ps #ps-aux
``` sh
ps # will show processes launched in our current terminal window or session

ps ax # will show all processes

ps aux # the u will display the information in a user-oriented format
```
Note: #ps has two ways it accepts options. With a dash is using Linux syntax and without is using BSD syntax. The two are not equivilant so running **-a** and **a** will have different results. 

**ps aux**: #ps-aux
``` sh
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0 169676 12932 ?        Ss   09:32   0:03 /sbin/init sp
```

**User**: The user the process is running under

**PID**: Process ID. Assigned to each process that is run on the system starting with 1.

**%CPU**: How much of 1 CPU core the process is using at the time the ps command is run. If you see 150% that means the process was using the full capacity of one core and 50% of the capacity of another. 

**%MEM**: How much total memory the process was using at the time the command is run. 

**START**: When the process was started

**TIME**: How much CPU time the process has used. Even if a process started 6 hours ago, it may have only run for 3 seconds and then sat in an idle state using 0% of the CPU for the remaining time. For the process to acrue 1 sec of time it needs to use 100% of the CPU for an entire second. 50% of one CPU core for 10 seconds will usually tanslate to 5 sec. 

**COMMAND**: This is where we're able to see the command that was used to start the process including any options. Process commands inside **square brackets** are running inside a privileged area of the Linux Kernel.

**top**: Shows processes dynamically, in order of most CPU intensive. #top 

**ps PID**: Display the process with the matching PID. #ps-pid
```sh
ps 1
    PID TTY      STAT   TIME COMMAND
      1 ?        Ss     0:03 /sbin/init splash

ps u 1 # display user-oriented
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0 169676 12932 ?        Ss   09:32   0:03 /sbin/init spla
```

**-U**: Display processes by a user #ps-U
```sh 
ps -U tom
    PID TTY          TIME CMD
   1690 ?        00:00:01 systemd
   1691 ?        00:00:00 (sd-pam)
  11951 ?        00:00:00 dbus-daemon
  12299 ?        00:00:00 gnome-keyring-d
..
```

**pgrep**: Process #grep #pgrep
```sh
pgrep -a syslog
853 /usr/sbin/rsyslogd -n -iNONE
# PID
```

**Nice Values**: Determines CPU priority. -20 to 19 with lower numbers being higher priority. Users can only set values between 0 and 19. Only root users can set values lower the 0.

**nice**: Sets the nice value of a command. #nice
``` sh
nice -n 11 bash # will launch bash with a nice value of 11
```

**renice**: Changes the nice value of a running process. #renice #nice #sudo Used for getting the process to run as a non-root user and having a different niceness value.
```sh
sudo renice [nice_value] [PID]
```
Note: You can only lower the value once per session. You can raise it as many times as you like. 

**l**: Running #ps with the l option will display the BSD long format which includes the nice values. #ps-l
``` sh
ps lax
F   UID     PID    PPID PRI  NI    VSZ   RSS WCHAN  STAT TTY        TIME COMMAND
4     0       1       0  20   0 169676 12932 -      Ss   ?          0:03 /sbin/ini
1     0       2       0  20   0      0     0 -      S    ?          0:00 [kthreadd
1     0       3       2   0 -20      0     0 -      I<   ?          0:00 [rcu_gp]
```
Note: Processes run by a process with a nice value will inheret it. 

**f**: forest. Shows us child and parent relationsips of processes
``` sh
ps fax 
    PID TTY      STAT   TIME COMMAND
..
    825 ?        Ss     0:03 /usr/sbin/acpid
    831 ?        Ss     0:00 avahi-daemon: running [ubuntu.local]
    909 ?        S      0:00  \_ avahi-daemon: chroot helper
..

```

**Signals**: Linux can send an application a signal which will typically make the application stop what it's doing and do what the signal instructs. #signal #kill

Not all applications respond to signals and need to have their responses coded in. However, two exceptions are the **SIGSTOP** and **SIGKILL** command.

**SIGSTOP**: Will halt a process #sigstop 

**SIGCONT**: Will resume a halted progress #sigstop #sigcont

**SIGKILL**: Will terminate a process #sigkill

**kill**: Used to send signals to applications #kill 
``` sh
kill -L # will list available signal commands

kill -SIGHUP or -HUP or -1 [PID]
```
Note: SIGHUP and HUP the signal number -1 will be the same command, you can ommit the SIG or use the number. 

Note: You can only send signals to process run by your current user. #sudo 

**pkill**: Use a process name instead of a PID. Can send signals to multiple processes. #pkill
``` sh
pkill -a bash
```

**CTRL + C**: Cancels the command. Also referred to as a Break Out #break-out
```sh 
sleep 120
^C 
```

**CTRL + Z**: Send command to the background. Pauses the command and it will make no progress.
``` sh
tom@ubuntu:~$ vim /etc/hostname

[1]+  Stopped                 vim /etc/hostname
tom@ubuntu:~$ fg # bring the command to the foreground
```

**Backgrounding**: To have a command run in the background, that is to not display it's progress but still run, you can use the **&** symbol at the end of the command
```sh
tom@ubuntu:~$ sleep 300 & # & sends commands to the background
[2] 21379 # provides us with the job number and the PID
```

**jobs**: View paused or backgrounded commands in terminal
```sh
tom@ubuntu:~$ sleep 300 &
[2] 21379
tom@ubuntu:~$ jobs
[1]+  Stopped                 vim /etc/hostname # stopped with CTRL + Z
[2]-  Running                 sleep 300 & # backgrounded by &
tom@ubuntu:~$ 
```

**fg**: Foreground. To return a command to the foreground use the **fg** command
``` sh
tom@ubuntu:~$ sleep 300 &
[2] 21379
tom@ubuntu:~$ jobs
[1]+  Stopped                 vim /etc/hostname
[2]-  Running                 sleep 300 &
tom@ubuntu:~$ fg 2
sleep 300
```

**bg**: Background. To resume a stopped command that was backgrounded using the **&**
``` sh
tom@ubuntu:~$ sleep 300 &
[2] 21379
tom@ubuntu:~$ jobs
[1]+  Stopped                 vim /etc/hostname
[2]-  Running                 sleep 300 &
tom@ubuntu:~$ fg 2
sleep 300
^Z
[2]+  Stopped                 sleep 300
tom@ubuntu:~$ bg 2
[2]+ sleep 300 &
tom@ubuntu:~$ jobs
[1]+  Stopped                 vim /etc/hostname
[2]-  Running                 sleep 300 &
tom@ubuntu:~$ 
```

**lsof**: List open files. Useful for seeing what files a process has open. #prgep #lsof #sudo
``` sh
tom@ubuntu:~$ pgrep -a bash
15347 bash
tom@ubuntu:~$ lsof -p 15347
COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF     NODE NAME
bash    15347  tom  cwd    DIR  259,2     4096  4325378 /home/tom
bash    15347  tom  rtd    DIR  259,2     4096        2 /
bash    15347  tom  txt    REG  259,2  1183448  9175708 /usr/bin/bash
..
```
Note: If you're running lsof on a process run by another user you will get an error. Make sure to run with #sudo 

You can also use **lsof** to see what process have a particular file or directory open. #sudo 
``` sh
tom@ubuntu:~$ pgrep -a syslog
853 /usr/sbin/rsyslogd -n -iNONE
tom@ubuntu:~$ sudo lsof /usr/sbin/rsyslogd
COMMAND  PID   USER  FD   TYPE DEVICE SIZE/OFF    NODE NAME
rsyslogd 853 syslog txt    REG  259,2   727248 9181318 /usr/sbin/rsyslogd
tom@ubuntu:~$ 

```