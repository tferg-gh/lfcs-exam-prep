Note all files and directories have an owner and only the owner or the root user can make changes to the ownership of a file. #ls #owner #sudo

**chown**: change owner of a file or directory #chown #sudo
``` sh
sudo chown jane family_dog.jpg # will change file owner to jane
```

**chgrp**: change the group of a file or directory. #chgrp
``` sh
chgrp [group_name] [file/directory] # You can only change to groups that the user is a part of
```

**groups**: view the groups that a user is a part of #groups #chgrp 
``` sh
groups
```

Chwon can also be used to change the group with the following syntax: #sudo #chown #chgrp 
``` sh
sudo chown [user]:[group] /path/to/file.jpg
```

**chmod**: change file permissions. #chmod #permissions
``` sh
chmod [permissions] [file/directory]

chmod u+x file.jpg # will add the execute permission to the user without effecting any other permissions

chmod g-x file.jpg # will remove the execute permission to the group without effecting any other permissions

chmod o=x file.jpg # will replace the existing other permissions with just the execute permission

chmod u+rw,g=r,o= file.jpg # you can chain commands by seperating them with commas
```

**suid**: set user ID. When set, file will execute as user. #suid #permissions-special
``` sh
╰─ touch suidfile   

╰─ ls -l suidfile         
-rw-rw-r-- 1 tom tom 0 Jun 20 11:36 suidfile
 
╰─ chmod u+s suidfile # sets user ID on this file

╰─ ls -l suidfile    
-rwSrw-r-- 1 tom tom 0 Jun 20 11:36 suidfile # captial S for no execute permission

╰─ chmod u+x suidfile

╰─ ls -l suidfile    
-rwsrw-r-- 1 tom tom 0 Jun 20 11:36 suidfile # change to lower case s
```

**sgid**: set group ID. When set, file will execute as group. #sgid #permissions-special
``` sh
╰─ touch sgidfile

╰─ chmod g+s sgidfile # sets group ID on this file

╰─ ls -l sgidfile 
-rw-rwSr-- 1 tom tom 0 Jun 20 11:44 sgidfile # capital S for no execute permission

╰─ chmod g+x sgidfile 

╰─ ls -l sgidfile 
-rw-rwsr-- 1 tom tom 0 Jun 20 11:44 sgidfile # change to lower case s
```

**sticky bit**: When set, only the user can delete the file or directory. #sticky-bit #permissions-special
``` sh
╰─ touch stickybit

╰─ ls -l stickybit 
-rw-rw-r-- 1 tom tom 0 Jun 20 11:49 stickybit

╰─ chmod o+t stickybit # set stickybit on file

╰─ ls -l stickybit    
-rw-rw-r-T 1 tom tom 0 Jun 20 11:49 stickybit # capital T for no execute permission

╰─ chmod o+x stickybit

╰─ ls -l stickybit    
-rw-rw-r-t 1 tom tom 0 Jun 20 11:49 stickybit # change to lower case t
```