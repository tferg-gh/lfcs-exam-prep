**> Output redirection**: Redirect the output of a command to somewhere else. By default output is displayed in the terminal. #redirect-output 

**> overwrite**: This will overwrite the existing file or create a new one. #redirect-output-overwrite
``` sh
cat file1 > output.txt # redirects the output to output.txt
```

**>> append**: This will add the output to the end of the file or create a new one. #redirect-output-append
```sh
cat file1 >> output.txt # appends the output to output.txt
```

**1> stdout**: This directs the standard output #redirect-output-stdout
``` sh
cat file1 1> output.txt # redirects the stdout to output.txt
```

**2> stderr**: This directs the standard error output #redirect-output-stderr
``` sh
cat file 1> stdout.txt 2> stderr.txt
```

**2>/dev/null**: Essentially delete errors. #redirect-output-stderr  #dev-null
``` sh
grep -r '^The' /etc/ 2>/dev/null # will redirect errors to /dev/null
```

**1> 2>&1**: Redirect errors to where you redirected standard output. #redirect-output-stdout  #redirect-output-stderr 
``` sh
grep -r '^The' /etc/ 1> all_output.txt 2>&1 # redirect errors to all_output.txt
```

**< Input redirection**: Use a file to pass information to a command #input-redirection
``` sh
sendemail someone@emailaddress.com < emailcontent.txt # simulates typing
```

**<< Heredoc**: Take input from here until **EOF**. Enter adds a new line. **EOF** can be replaced with anything, it just needs to end with the same pattern. #input-redirection #heredoc #EOF
```sh
sort <<EOF
1
3
2
6
4
5
EOF
1
2
3
4
5
6
```

**<<< Here String**: Similar to a #heredoc but only has a single line of text. #input-redirection  #herestring
``` sh
bc <<<1+2+3+4
10
```

**| piping output**: Use the **|** pipe to send output from one command to another. #pipes #redirect-output 
``` sh
grep -v '^#' /etc/login.defs | sort # finds all uncommented lines and sorts them
```