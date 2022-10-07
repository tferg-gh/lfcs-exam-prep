**grep**: Search through text files #grep #egrep #redirect-output #pipes #regex 
``` sh
grep [options] 'search_pattern' [file] # also works with piped content

grep 'CentOS' /etc/os-release # return only text matching the search pattern

grep -i 'CentOS' /etc/os-release # -i = case insensitive

grep -r 'CentOS' /etc/ # -r = recursive. Use to search through directories

grep -v 'CentOS' /etc/os-release # -v = invert match. Display text that doesn't match

grep -w 'red' /etc/os-release # -w = word. Match on only whole words

grep -oi 'red' /etc/os-release # -o = only-matching. Outputs only the matching words
```

