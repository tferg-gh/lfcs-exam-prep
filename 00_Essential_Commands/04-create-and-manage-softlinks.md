**ln -s**: Create a symbolic link. #ln 
```
ln -s [path/to/file] [path/to/link]
```

``` sh
╰─ ls -l /home/tom/Desktop
total 0
lrwxrwxrwx 1 tom tom 37 Jun 20 10:39 switching_routing_shortcut -> /home/tom/Documents/switching_routing
```
Note the "l" at the beginning of the file permissions denotes a link #ln-s-permissions

Note if you change the name of any of the directories of a symbolic link, the link will break. #ln-s-broken-link

**readlink**: Display the path of a symbolic link
``` sh
╰─ readlink /home/tom/Desktop/switching_routing_shortcut 
/home/tom/Documents/switching_routing
```

Note you can softlink to files or directories and you can also link to files and directories on other filesystems as opposed to how hardlinks work. #ln 

[[03-create-and-manage-hardlinks]]