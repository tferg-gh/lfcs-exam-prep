**Display boot target**: #get-default 
``` sh
systemctl get-default
graphical.target # configured to boot into a GUI
```

**Change boot target**: #set-default 
```sh
sudo systemctl set-default multi-user.target # skips loading GUI
```

**Switch boot target**: To the GUI #isolate #graphical-target 
```sh
sudo systemctl isolate graphical.target # load GUI for this session
```

**Emergency target**: Loads minimal services. #emergency-target  
```sh
sudo systemctl isolate emergency.target # load into safe-mode for debugging
```
Root file system is set to read-only #root 

**Rescue target**: Less services than the multi-user target but more than the emergency target #rescue-target 
``` sh
sudo systemctl isolate rescue.target
```

Note: for the #rescue-target and the #emergency-target you must have a password set for the #root user.

#sudo #systemctl #get-default #set-default #isolate #graphical-target #multi-user-target #emergency-target #rescue-target 