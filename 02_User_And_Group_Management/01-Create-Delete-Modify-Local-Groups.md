# Local Groups
Note: Users that are a part of the WHEEL group are allowed to run applications as #sudo 

#### Primary Groups
A primary group is used when the user runs an applications or creates a file, they run or create the file as this user and group. 

## List
###### List the groups a user is part of #groups 
```sh
groups [user_name]
```
The first group after the colon is the primary group 
## Create
###### Create a new group #groupadd
```sh
sudo groupadd developers
```
## Delete
###### Remove a user from the group #gpasswd-delete
```sh
sudo gpasswd --delete [user_name] [group_name]
```
###### Delete a group #groupdel
```sh
sudo groupdel [group_name] 
```
Cannot be removed if group is a users primary group
## Modify
###### Add a user to a group #gpasswd-add
```sh
sudo gpasswd --add [user_name] [group_name]
```

###### Change a users primary group #usermod-gid
```sh
sudo usermod --gid [group_name] [user_name]
```

###### Change a users secondary group #usermod-G 
```sh
sudo usermod -G [group_name] [user_name]
```

###### Change a groups name #groupmod-new-name
```sh
sudo groupmod --new-name [new_name] [old_name]
```