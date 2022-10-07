# Package Managers
## Dnf 
These commands should also work for Yum

###### Check for upgrades #dnf-check-upgrade
``` sh
dnf check-upgrade # CentOS
```

###### Install ugprades #dnf-install-upgrade 
``` sh
sudo dnf upgrade
```

###### List repositories #dnf-list-repo-core
``` sh
sudo dnf repolist # use -v to list more information like the web addresses
```
###### List hidden repositories #dnf-list-repo-optional 
```sh
sudo dnf repolist --all # displays optional repositories
```

###### Enable an optional repository #dnf-enable-repo
``` sh
sudo dnf config-manager --enable [name_of_repo]
```
###### Disable an optional repository #dnf-disable-repo
``` sh
sudo dnf config-manager --disable [name_of_repo]
```
###### Install a third-party repository #dnf-install-repo
``` sh
sudo dnf config-manager --add-repo [address_to_repo]
```

###### Remove a third-party repository #dnf-remove-repo
``` sh
# list the repos
sudo dnf repolist -v

# identify the file the repo is stored in
Repo-filename    : /etc/yum.repos.d/docker-ce.repo

# then remove that file
sudo rm /etc/yum.repos.d/docker-ce.repo
```

###### Search for a package #dnf-search-package
``` sh
sudo dnf search [search_pattern]
```

###### List information of a package #dnf-list-package-info
```sh
sudo dnf info [package_name]
```

###### Install a package #dnf-install-package
```sh
sudo dnf install [package_name]
```

###### Reinstall a package #dnf-reinstall-package
```sh
sudo dnf reinstall [package_name]
```

###### Remove a package #dnf-remove-package
``` sh
sudo dnf remove [package_name]
```

###### Remove orphaned dependencies #dnf-remove-package-dependencies
``` sh
sudo dnf autoremove
```

###### List groups #dnf-list-group 
```sh
sudo dnf group list
```
A group is a collection of applications and dependencies

###### List hidden groups  #dnf-list-group-hidden
``` sh
sudo dnf group list --hidden
```

###### Install packages from a group #dnf-install-group
``` sh
sudo dnf group install '[group_name]'
```
It's important to wrap the group name in single quotes.

###### Install optional packages from a group #dnf-install-group-optional
``` sh
sudo dnf group install --with-optional '[group_name]' 
```

###### Remove packages from a group #dnf-remove-group
``` sh
sudo dnf group remove '[group_name]'
```

###### Installing a package from a file #dnf-install-package-file
``` sh
# Requires and rpm file, which is similar to a tar archive
sudo dnf install ./[rpm_package.rpm]
```
Note how there is a ./ before the package. Remove packages as normal #dnf-remove-package 

###### List package manager history #dnf-list-history
```sh 
sudo dnf history
```

###### Identify the package a file belongs to #dnf-list-provides-file
```sh
dnf provides /etc/anacrontab 
```

###### Identify a package a command belongs to #dnf-list-provides-command
```sh
dnf provides docker # docker is the command 
```


###### List files in a package #dnf-list-package-files
``` sh
dnf repoquery --list nginx # will list the files present in the package
```
Useful for finding the config file locations foran application