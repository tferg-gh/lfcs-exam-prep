**find**: Use to find files that match criteria #find
``` sh
find [path/to/directory] [type] [criteria]

find /usr/share/ -name '*.jpg' # will find all files with .jpg in the name
```

**-name**: Files based on name #find-name
``` sh
find -name file # case sensitive
find -iname file # case insensitive
```

**-mmin**: Files modified in minutes #find-mmin
```sh
find /var/log/ -mmin 5   # list files modified in the minute, 5 min ago
find /var/log/ -mmin -5  # list files modified in the last 5 min
find /var/log/ -mmin +5  # list files mofified in everything but the last 5 min
```

**-mtime**: Files modified in 24 our periods #find-mtime
``` sh
find /var/log -mtime 0  # list files in the last 24 hours
find /var/log -mtime 1  # list files between 24 and 48 hours
find /var/log -mtime 2  # list files between 48 and 72 hours
```

**-cmin**: Files changed in minutes #find-cmin
```sh
find /var/log/ -cmin 5   # list files changed in the minute, 5 min ago
find /var/log/ -cmin -5  # list files changed in the last 5 min
find /var/log/ -cmin +5  # list files changed in everything but the last 5 min
```

**Change vs Modified**: Change time refers to metdata changes, while modified time refers to content changes. #change-time #modified-time #find-mmin #find-mtime #find-cmin 

**-size**: Files based on size #find-size
```sh
find /var/log/ -size 512k   # list files that are exactly 512kb
find /var/log/ -size -512k  # list files less than 512kb
find /var/log/ -size +512k  # list files greater than 512kb
```

**AND**: Combining find queries where both conditions are true #find-and
``` sh
find /var/log/ -size +512k -iname "f*" # find files matching X and Y
```

**OR**: Combining find queries where either condition is true #find-or
``` sh
find /var/log/ -size +512k -o -iname "f*" # find files matching either X or Y
```

**NOT**: Exclude from find queries where conditions are true #find-not
``` sh
find /var/log -not -size +512k # find files that don't match X 
```

**-perm**: Files with permissions #find-perm
``` sh
find /var/log/ -perm u=rwx,g=rw,o=r # find files with these exact permissions
find /var/log/ -perm -u=r           # find files with at least these permissions
find /var/log/ -perm /u=rwx         # find files with any of these permissions
```