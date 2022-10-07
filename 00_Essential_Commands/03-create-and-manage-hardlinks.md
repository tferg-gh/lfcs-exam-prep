**stat**: Display metadata about a file. #stat #ln 
``` sh
╰─ stat switching_routing 
  File: switching_routing
  Size: 1194      	Blocks: 8          IO Block: 4096   regular file
Device: 10302h/66306d	Inode: 4329325     Links: 1 # nubmer of hard links
Access: (0664/-rw-rw-r--)  Uid: ( 1000/     tom)   Gid: ( 1000/     tom)
Access: 2022-05-26 08:52:17.025580064 +1000
Modify: 2022-05-26 08:52:17.025580064 +1000
Change: 2022-05-26 08:52:17.025580064 +1000
 Birth: -
```

**ln**: Create a hardlink #ln #chmod
``` sh
ln [path/to/target] [path/to/link] # can only hardlink to files and not directories
# Can also only create hardlinks in the same filesystem.
# Permissions apply to Inode
```

[[04-create-and-manage-softlinks]]
