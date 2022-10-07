**cat**: Display contents of a file #cat #tac
``` sh
cat /home/tom/Documents/small_file.txt # useful for small files 
```

**tac**: Display contents of a file starting from the last line #cat #tac
``` sh
tac /home/tom/Documents/small_file.txt # useful for small files 
```

**tail**: Display the last few lines of a file #tail #head
``` sh 
tail /var/log/dnf.log        # shows last 10 lines by default
tail -n 20 /var/log/dnf.log  # shows last 20 lines
```

**head**: Display the first few lines of a file #head #tail 
``` sh 
head /var/log/dnf.log        # shows first 10 lines by default
head -n 20 /var/log/dnf.log  # shows first 20 lines
```

**sed**: Stream editor. Edits the text in a file #sed #regex #redirect-output
``` sh
sed 's/canda/canada/' userinfo.txt   # replace text in first match on line
sed 's/canda/canada/g' userinfo.txt  # replace all instances of canda
sed 's/canda/canada/gi' userinfo.txt # replace all instances regardless of case
sed -i 's/canda/canada/gi' userinfo.txt # save changes in place
```

**cut**: Used to extract information from a file #cut #redirect-output 
``` sh
cut -d ' ' -f 1 userinfo.txt # -d = delimiter -f = field 
```

**uniq**: Remove non-unique adjacent lines  #uniq #sort #redirect-output 
``` sh
cat countries.txt 
Australia
Canada
Australia
Australia
Canada

uniq countries.txt # removes non-unique adjacent lines

cat countries.txt
Australia
Canada
Australia
Canada
```

**sort**: Sorts lines alphabetically #sort #uniq #pipes #redirect-output 
``` sh
cat countries.txt 
Australia
Canada
Australia
Australia
Canada

sort countries.txt # this doesn't change the file
Australia
Australia
Australia
Canada
Canada

sort countries.txt | uniq > sorted_countries.txt

cat countries.txt 
Australia
Canada
```

**diff**: Displays the differences in two files #diff #sdiff
``` sh
╰─ diff file1 file2 
1c1
< Only exists in file 1
---
> Only exists in file 2
4c4
< Only exists in file 1
---
> Only exists in file 2

╰─ diff -c file1 file2 # -c for context
*** file1	2022-06-20 14:21:10.215135852 +1000
--- file2	2022-06-20 14:21:25.943392444 +1000
***************
*** 1,4 ****
! Only exists in file 1 # ! denotes a change +/- denotes additional or missing 
  Identical line 2
  Identical line 3
! Only exists in file 1
--- 1,4 ----
! Only exists in file 2 
  Identical line 2
  Identical line 3
! Only exists in file 2

```

**sdiff**: Displays the differences between two files side-by-side #sdiff #diff
``` sh
sdiff [file1] [file2] # can also be accomplished with diff -y
```

