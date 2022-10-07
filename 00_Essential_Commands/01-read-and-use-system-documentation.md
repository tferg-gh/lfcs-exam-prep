**--help**: Typically used to get a quick snapshot of information about a terminal command including use and common switches. #help

``` sh
ls --help
```

**man**: Opens the manual for the command. This contains much more information about the command, how to use it and typically where to find more information. #man

``` sh
man journalctl
```

Note: To find man pages about commands with the same name, use the man man page to see the different type. #man-types

``` sh
man 1 printf # displays the manual page for the program/command of printf
```

**apropos**: allows you to search through the short description of man pages. #man-apropos

``` sh
apropos director # returns all commands with director in short description
```

**mandb**: build the database for #man-apropos. Typically when you have a new system the database has not been built yet. #man-mandb

``` sh
sudo mandb
```

