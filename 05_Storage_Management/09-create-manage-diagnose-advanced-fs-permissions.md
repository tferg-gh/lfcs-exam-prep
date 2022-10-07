##### setfacl
Set file access control list. Used for specifying granular file permissions for 1 or more users.

```sh
sudo setfacl --modify user:aaron:rw examplefile
```

Files with a + at the end of the file permissions when doing a `ls -l` have an acl attached to them.

```sh
getfacl exmaplefile
```

Note: Mask refers to the maximum file permissions this file can have. 

```sh
sudo setfacl --modify mask:r examplefile # -m
```

This will set the mask of the file to `read-only` restricting other users access where they may have previously had `write` or `execute` permissions.

If you use `getfacl` on the file and the mask has been set, and users, groups or others have permissions higher than the mask, you'll see an `#effective:r--` against the permission.

```sh
sudo setfacl --remove user:aaron examplefile
```

This will remove the ACL for user aaron. 

```sh
sudo setfacl --recursive -m user:aaron:rwx dir1/
```

This will set the ACL permissions for aaron on the directory and all the files in the directory. 

```sh 
sudo setfacl --recursive --remove user:aaron dir1/
```

This will remove the ACL for user aaron on the directory and all the files in it. 

##### chattr
Change file and directory attributes. Turning these on or off makes the file or directory behave a certain way. 

```sh 
sudo chattr +a newfile
```

This will add the `append only` attribute to this file. We can keep adding data to the file but we can never change what already exists there. (Allows `>>` but not `>` )

```sh
sudo chattr -a newfile
```

This will remove the `append only` on the file. 

```sh 
sudo chattr +i newfile
```

This will make the file immutable. This means it cannot be changed in any way by any users. Even the root user.

```sh 
lsattr newfile
```

This will list the attributes of a file.