**ls**: list files in your current directory #ls
``` sh
ls 
ls -a # list all files including hidden files
ls -l # list files in the long format including file permissions and size
ls -lh # list files and directories in the long format with human readable sizes
ls -alh 
```

**cd**: Change directory. #cd
``` sh
cd /var/log/ # this would change our current working directory to /var/log/
cd .. # this will take us one level higher
cd ../../Documents # this will take use two levels higher and into Documents
cd Documents/Invoice.pdf # this assumes /home/tom/Documents/Invoice.pdf because we're currently in /home/tom/. Considered relative
cd / # go to root directory
cd - # go to previous working directory
cd ~ # go to home directory. Can also use just cd
```

**touch**: Create a new file or update existing file. #touch
``` sh
touch Invoice.pdf # the created file will be empty
```

**mkdir**: Create a new directory. #mkdir
``` sh
mkdir /home/tom/Documents/Work/ # will make the Work directory
```

**cp**: copy a file. #cp
``` sh
cp [source] [target]
cp Invoice.pdf /home/jane/Documents/Invoice.pdf # files don't have to be the same
cp -r /path/to/source/. /path/to/target/ # use the . at the end of the dir to copy the contents and not the source folder 
```

**cp -r**: copy a directory #cp-r
```sh
cp -r Documents/ /home/jane/ # -r means recursive. Use to copy a directory

# Note Directory must not exist at target for copying a directory, otherwise it will place in the existing directory
```

**mv**: move a file. Does not leave a copy behind. #mv
``` sh
mv [source] [target]
```

**rm**: Delete a file. #rm
``` sh
rm Invoice.pdf # Will delete the file
```

**rm -r**: Delete a directory and all it's contents. #rm-r
``` sh
rm -r Documents/
```