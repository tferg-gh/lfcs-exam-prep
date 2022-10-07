**reboot** #reboot
``` sh
sudo systemctl reboot
```

**poweroff** #shutdown
``` sh
sudo systemctl poweroff
```

**--force**: To force a reboot or shutdown #reboot-force #shutdown-force
``` sh
sudo systemctl reboot --force
sudo systemctl poweroff --force
```

**--force --force**: To **really** force a shutdown or reboot #reboot-force #shutdown-force 
```
sudo systemctl reboot --force --force
sudo systemctl poweroff --force --force
```

**shutdown**: To schedule a shutdown or reboot. #reboot #shutdown 
``` sh
sudo shutdown 02:00 # set the system to shutdown at 2am, uses 24hr time

OR

sudo shutdown +15 # set the system to shutdown in 15min

OR

sudo shutdown -r 02:00 # -r = reboot
```

**wall message**: So users are aware a shutdown or reboot is coming and gives them a chance to save their work #shutdown #reboot 
``` sh
sudo shutdown -r +15 'Scheduled restart in 15min, save work and log off'
```