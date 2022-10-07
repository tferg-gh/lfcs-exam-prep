###### autofs
Used to configure auto-mounting for directories. Useful for network shares so you only need to mount the directories when they're being accessed. Saves on bandwidth and reduces pressure on the server.
**Install**
``` sh
sudo dnf install autofs
```
**Start**
``` sh
sudo systemctl start autofs.service
```
**Enable**
``` sh
sudo systemctl enable autofs.service
```
**Configure master**
``` sh
/etc/auto.master # Configures the automount share dir, the location of the share config file and the timeout
```

**Example**
`/shares/ /etc/auto.shares --timeout=400`. 

Use directory `/shares/` for automounting (will autocreate if it doesn't exist). You can also use `/-` to say there is no parent directory and to mount directly into the directory. If you're doing this you need to specify an absolute path in the `/etc/auto.shares`

Define the file that contains the auto-mounting share information at `/etc/auto.shares` and finally set the timeout to 400 seconds.

**Configure shares**
``` sh
/etc/auto.shares # mount the network share on demand 
```

**Example**
`mynetworkshare -fstype=auto 127.0.0.1:/etc` 

When `/mynetworkshare/`  is accessed, the on-demand mount should be applied. The `/shares/` directory defined in the `auto.master` file acts as the root so this directory would actually be `/shares/mynetworkshare/`.  

The `-fstype=auto` makes autofs try to automatically detect the `fstype` but if we know it we can define it like `-fstype=nfs4`. There are many options here and you can have multiple, such as `-fstype=auto,ro` will set it to auto and read-only. 

`127.0.0.1:/etc` is the location of our nfs share. This tells autofs to mount the directory from the NFS server that can be found at that IP address. You can also use a hostname i.e. `nfs1.example.com:/etc`) or you can do local filesystems by ommitting the IP/hostname i.e. `:/dev/vdb2`

**Restart the service after making changes**
``` sh
sudo systemctl reload autofs.service
```

###### nfs
Network file sharing daemon. 

**Install**
``` sh
sudo dnf install nfs-utils
```
**Start**
``` sh
sudo systemctl start nfs-server.service
```
**Enable**
``` sh
sudo systemctl enable nfs-server.service
```
**Configure**
``` sh
/etc/exports # which files to share on the network
```

`/etc 127.0.0.1(ro)` the `/etc` directory should be shared to computer with the IP address `127.0.0.1`, so the local host and clients will have `read only` access

**Restart the service after making changes**
``` sh 
sudo systemctl reload nfs-server.service # after making changes to /etc/exports
``` 