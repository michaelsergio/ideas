# Terminal Icons
OSX includes emoticons in unicode MISCELLANEOUS_SYMBOLS_AND_PICTOGRAPHS block.
I want to see icons in ls.

## Implementation

Create a .terminalicons file in home that has rules specific file names.
Create another file for mime-type lookups.

alias ls = ls OPTIONS | iconls 

iconls replaces filenames from ls output with .terminalicons and the other mimetype files replacement rules.
 
``` bash
$ ls 
🍺  a-secret-recipe.txt
   noicon.md
🔠  simple-text.txt
📱  work.m
```

## Icon Setter
dd
Another tool should let me set the icon.
```
set-icon noicon [ICON_NAME]
```
If ICON_NAME not set display curses app selector.
[unicode-icons](http://www.fileformat.info/info/unicode/block/miscellaneous_symbols_and_pictographs/utf8test.htm)
