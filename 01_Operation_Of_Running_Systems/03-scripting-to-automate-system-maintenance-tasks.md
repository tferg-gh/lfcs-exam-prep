**bash**: Born Again Shell. Command interpreter.

It is #best-practice to add the **.sh** extension to script files for easy identification unless they're for use in other application such as #cron. 

**#!**: Shebang. Goes at the begining of bash scripts. Followed by the path to the Bash binary. 
``` sh
#!/bin/bash
```

**#**: This denotes a comment in a bash script and the interpreter will ignore these lines. #best-practice to comment your code so you understand what it does.
```sh
#!/bin/bash

#Log the data and time the script was last executed
date >> /tmp/script.log
cat /proc/version >> /tmp/script.log

```

**permissions**: To run a script the user needs execute permissions for the file. #chmod 
``` sh
chmod u+x script.sh 

or

chmod +x script.sh # this provides execute permissions for everybody, user, group, and others
```

**run the script**: 
``` sh
/home/tom/script.sh # full path to script

or 

./script.sh # relative path must have ./ 
```

**built-ins**: you can build smarter scripts using these as they provide additional logic #built-ins
``` sh
help # provide a list of available built-ins

help if # provides information about how to use the if built-in
if: if COMMANDS; then COMMANDS; [ elif COMMANDS; then COMMANDS; ]... [ else COMMANDS; ] fi
    Execute commands based on conditional.
    
    The 'if COMMANDS' list is executed.  If its exit status is zero, then the
    'then COMMANDS' list is executed.  Otherwise, each 'elif COMMANDS' list is
    executed in turn, and if its exit status is zero, the corresponding
    'then COMMANDS' list is executed and the if command completes.  Otherwise,
    the 'else COMMANDS' list is executed, if present.  The exit status of the
    entire construct is the exit status of the last command executed, or zero
    if no condition tested true.
    
    Exit Status:
    Returns the status of the last command executed.

help test
test: test [expr]
    Evaluate conditional expression.
    
    Exits with a status of 0 (true) or 1 (false) depending on
    the evaluation of EXPR.  Expressions may be unary or binary.  Unary
    expressions are often used to examine the status of a file.  There
    are string operators and numeric comparison operators as well.
    
    The behavior of test depends on the number of arguments.  Read the
    bash manual page for the complete specification.
    
    File operators:
	..
	-f FILE        True if file exists and is a regular file.
	..
```

**if/test**: This is a built in that we can use to add some additional logic to our scripts. #built-ins-if #built-in-test
```sh 
#!/bin/bash
# If a backup exists, move it to .OLD and make a new backup, otherwise make a new backup.
if test -f /tmp/archive.tar.gz; then # -f True if file exists and is a reg file
	mv /tmp/archive.tar.gz /tmp/archive.tar.gz.OLD
	tar --create --auto-compress --file /tmp/archive.tar.gz /etc/dnf/ # caf
else
	tar --create --auto-compress --file /tmp/archive.tar.gz /etc/dnf/ # caf
fi
```

Also consider looking further into other #built-ins such as #built-ins-for, #built-ins-while and function variables.

A good #example file to refer to if you need a quick refresher of how scripts work, look at this file:
``` sh
cat /etc/cron.hourly/0anacron # not always at this dir
```

Also, refer to the Shell Scripts for beginners course on KodeKloud.