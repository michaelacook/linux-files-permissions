# File Globs
- [Bash Globbing Tutorial](https://linuxhint.com/bash_globbing_tutorial/)
- Actions can be performed on *globs* of files at once using patterns and wild cards
- "The process of expanding a nonspecific file name containing wildcard characters in specific file names"
- The `*` wildcard matches zero or more of any character 
- The `?` wildcard matches exactly one of any character
    - To match more than one character, you can use more than one `?`
      - ie. `ls file??.txt`
- Passing a character set pattern for a wildcard allows you to match specific characters
  - ie. `mv file[123].txt ..` will move all files starting with `file` having either a 1, 2 or 3 in the name, then `.txt`
- To pass a range into a character set use a hyphen 
  - ie. `cp file[1-99].txt` will match files `file1.txt` through `file99.txt`
  - ie. `ls file[a-zA-Z].txt` will match upper-case and lower-case 
  - ie. `mv file[0-9abc].txt ..` 
- To match a hyphen, the hyphen character must be included at the beginning of the character set 
  - ie. `file[-0-9].txt`
- Negate a character by placing a `^` or `!` at the beginning of a character set

[Previous](getting-information-on-files.md)|[Next](character-classes.md)