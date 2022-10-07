**less**: Open a file in a feature rich pager #less #more #pager
```
less [file1]
```

Use Arrow Keys **Up** and **Down** to navigate through the document. 

Use **/** to search and **N / Shift + N** to navigate to next and last search matches. Pass **-I** to make the search case insensitive.

Use **Q** to quit

**more**: Open a file in a simple pager #more #less #pager 
```
more [file1]
```

Use the **spacebar** to display the next page and **Q** to quit

**vim**: Vi Improved. Mode sensitive text editor. #vim #vi #pager 
```
vim [file1]
```

Press **i** to enter insert mode to add text. **Escape** to exit insert mode.

Use **/** to search and **N / Shift + N** to navigate to next and last search matches. Use **\\c** at the end of the search term for case insensitive.  

**:1** takes you to line 1. **:set number** enables line numbers

**yy** will copy a line

**p** will paste the copied data

**dd** will cut a line

**:q** to quit, **:q!** to force quit, **:w** to write changes, **:wq** to write changes and quit, **:x** will also save and exit