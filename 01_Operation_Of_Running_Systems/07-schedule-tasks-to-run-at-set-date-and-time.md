#cron #anacron #at 

###### Cron
``` sh
tom@ubuntu:~$ cat /etc/crontab
# /etc/crontab: system-wide crontab

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name command to be executed
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly

```

``` sh
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
```

The first five values here tell #cron **when** a job is supposed to be run. The sixth value is a **username** and this is followed by the **command**. 

``` sh
[time_date] [user_name] [COMMANDS]
```

**Time & Date**

The first five values representing the time from left to right are, minutes, hours, day of the month, month and day of the week. 

The wildcard * matches all possible values (i.e. every hour)

You can specify multiple values if you seperate them with a comma (i.e. 15,45 every 15th and 45th minute). Note there is no space between the values. 

You can specify a range using a dash between the two values (i.e. 2-4 will run on the 2nd, 3rd and 4th hour)

You can specify a step using the forward slash /. By default if you have an asterix in the hour field it will step every 1 hour, but if you added a forward slash afterward you could specify it to run every 4 hours. (i.e. \*/4 would be run every 4th hour).

You can combine ranges with steps, if you want to run a command every 4 hours at midnight, 4am, 8am and noon you would use 0-8/4

Scripts in these directories will run hourly, daily, weekly or monthly respecitvley. #sudo 

#crontab-hourly     /etc/cron.hourly/
#crontab-daily       /etc/cron.daily/
#crontab-weekly   /etc/cron.weekly/
#crontab-monthly /etc/cron.monthly/

###### Considerations
- You must omit the .sh extension from a shellscript you want to use as a cronjob.
- The script must have read and execute permissions #chmod 
- You must use sudo to copy files into these folders #sudo
- You can remove jobs simply by moving the script from the directory.
- Always use the full path to the binary in the commands #which 

**System-wide Table vs User Table**
/etc/crontab is the system-wide table, to access and update the users table you should use:
``` sh
crontab -e
```
Using this will not display or require a user. The user is inferred by whoever ran the command.

``` sh
35 6 * * * /usr/bin/touch test_passed
```
This would run every day at 6:35am and touch the test_passed file. 

##### List cronjobs
```sh 
crontab -l
```

This will #cat the crontable for your user. 

##### List or edit cronjobs for other users
``` sh
sudo crontab -l # list root user
sudo crontab -e # edit root user

sudo crontab -e -u jane # edit other user
```
This will list or edit the crontab for the root user or if you specify it using the -u option, another user.

###### Remove a cronjob
```sh
crontab -r # remove all
crontab -r 20 # remove this specific job
sudo crontab -r -u jane # remove all jobs for another user
```
This will remove the crontable for the user or for another user with the -u option. 

###### Anacron
```sh
tom@ubuntu:~$ cat /etc/anacrontab
# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
HOME=/root
LOGNAME=root

# These replace cron's entries
1	5	cron.daily	run-parts --report /etc/cron.daily
7	10	cron.weekly	run-parts --report /etc/cron.weekly
@monthly	15	cron.monthly	run-parts --report /etc/cron.monthly
```
The first number decides how often it should run in days, the second is the delay between running each job in minutes, the job identifier, can be anything and finally the command. 

You can set the run period using numbers or @weekly, @monthly.

###### Test Anacron
``` sh
anacron -T
```
This will show you any errors before the jobs run.

###### At
``` sh
at 15:00 # time
at > /usr/bin/touch file_created_by_at

at 'August 20 2022' # date
at > /usr/bin/touch file_created_by_at

at '2:30 August 20 2022' # date & time
at > /usr/bin/touch file_created_by_at

at 'now +30 minutes' # relative times inc. hours, days, weeks, months
at > /usr/bin/touch file_created_by_at
```
Press **Enter** to go to an **empty line**, then **Ctrl + D** to save the job #at 

###### List scheduled jobs with atq
``` sh
atq
20        Wed Nov 17 08:30:00 2022 a tom
```

###### Display the scheduled command
``` sh
at -c 20 # where the number is the Job ID
```
The first number is the job ID and can be used to see what an **at** job contains using the **-c** option

###### Remove a scheduled job
``` sh
atrm 20 # where the number is the Job ID
```
To remove a job you need the Job ID as well and use **atrm**

