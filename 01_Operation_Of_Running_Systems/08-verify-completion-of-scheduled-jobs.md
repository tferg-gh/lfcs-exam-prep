###### Cron log locations
``` sh
sudo grep 'cron' /var/log/cron 
sudo grep 'anacron' /var/log/cron 
sudo grep 'atd' /var/log/cron # atd = at daemon
OR
sudo grep 'cron' /var/log/messages
OR
sudo grep 'cron' /var/log/syslog
OR 
sudo journalctl -u cron.service
```
Displays the logs for the scheduled cronjobs

###### Force Anacronjobs to run
``` sh
sudo anacron -n # will run all jobs scheduled for today
sudo anacron -n -f # will run all jobs again even if they've already been run
```

###### Add output to the system journal
``` sh
at 'now +1 minute'
at> echo "My at job produced this output" | systemd-cat --identifier=at_scheduled_output
```
Piping output to the systemd-cat command and providing it with an identifier will log the output in the journal. 

