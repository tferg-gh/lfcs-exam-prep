**tar**: tape archive. Packs multiple files into a single file. #tar

**tar --list**: List the contents of an archive #tar-list
``` sh
tar --list --file archive.tar
file1
file2
file3
tar -tf archive.tar # does the same thing
tar tf archive.tar # does the same thing
```

**tar --create**: Create new archive #tar-create
``` sh
tar --create --file archive.tar file1

OR

tar --create --file archive.tar directory/ # using a relative path will store as so
directory/file1
directory/file2

tar --create --file archive.tar /home/tom/Documents/directory/ # using absolute
/home/tom/Documents/directory/file1
/home/tom/Documents/directory/file2
```

**tar --append**: Add to existing archive #tar-append
``` sh
tar --append --file archive.tar file1
```

**tar --extract**: Unpack the archive #tar-extract
``` sh
tar --extract --file archive.tar # will extract to directories listed in archive
```

It is best practice to list the files in an Archive first before extracting them so you know where they go. #best-practice

By default tar extracts to your current working directory. To extract to another directory use: 
``` sh
tar --extract --file archive.tar --directory /path/to/extract/
```

It is also best practice to extract and archive information using **sudo** so all the permissions are retained. #sudo #best-practice 

[[13-compress-and-uncompress-files]]
