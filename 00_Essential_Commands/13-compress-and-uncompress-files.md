**gzip, bzip2, xz**: Compression tools typically installed on most Linux distros. Commands are mostly the same so I'm lumping them together. #compression #tar #gzip #bzip2 #xz
``` sh
gzip file1
```

**--keep**: By default the file is deleted after being compressed. This will keep the file. #gzip-keep
```sh 
gzip --keep file1.gz
```

**--list**: Lists the compressed file contents. #gzip-list
```sh
gzip --list file1.gz
```

**--decompress**: Extract an archive from a file. #gzip-decompress
```sh
gzip --decompress file1.gz

or 

gunzip file1.gz # does the same thing as --decompress
bunzip file1.bz2
unxz file1.xz
```

**--test**: Test the archive to make sure it has no errors #gzip-test
```sh
gzip --test file1.gz
```

**zip**: Another compression tool, unlike gzip, zip can be used to archive an entire directory instead of only individual files. #zip #gzip 
``` sh
zip archive file1 # will append .zip to the end of the file

zip -r archive Pictures/ # -r for recursive
```

**unzip**: Decompress archive file that has been compressed using zip. #zip 
``` sh
unzip archive.zip
```

**tar --autocompress**: Compresses a .tar archive using whichever file extension matches the available tool. #tar #gzip #bzip2 #xz #zip #compression 
``` sh
tar --create --autocompress --file archive.tar.gz file1
```

**tar --extract**: Tar can intelligently decompress the file based on the file extension #tar-extract 
``` sh
tar --extract --file archive.tar.gz
```

[[12-archive-backup-compress-unpack-uncompress-files]]