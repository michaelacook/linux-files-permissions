# File Globs
- [Bash Globbing Tutorial](https://linuxhint.com/bash_globbing_tutorial/)
- `man 7 glob` to read about file globbing
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

## Character classes
- In addition to using character set patterns, you can also use character classes 
- A character class is a grouping of like characters, such as letters, numbers, or punctuation 
  
|Class|Match|Result|Equivalent|
|-|-|-|-|
|[:digit:]|Whole Numbers|1,2,3|[0-9]|
|[:upper:]|Uppercase Letters|A,B,C|[A-Z]|
|[:lower:]|Lowercase Letters|a,b,c|[a-z]|
|[:alpha:]|Uppercase & Lowercase| a,b,C|[a-zA-Z]|
|[:alnum:]|Uppercase, Lowercase & Numbers|a,B,9|[a-zA-Z0-9]|
|[:space:]|Tab, Newline, Vertical Tab, Form Feed, Carriage Return, & Space|||
|[:graph:]|Printable Characters, not including Spaces|||
|[:print:]|Printable Characters, including Spaces|||
|[:punct]|Punctuation|!,?,~|[-!"#$%&'()+,./:;<=>?@[\]^_`{|}.]|
|[:cntrl:]|Nonprintable Control Characters|||
|[:xdigit:]|Hexadecimal Characters|0-9, A-F, a-f|[0-9A-Fa-f]|

- To use a character class use it inside a character set
  - ie. `ls file[[:digit:]]`
  - ie. `ls file[[:digit:][:space:]]`
  - ie. `ls file[![:alnum:][:punc:]].txt - match any pattern *not* alphanumeric or punctuation

[Previous](getting-information-on-files.md)|[Next](brace-expansion.md)