# Getting Information on Files
- All files have metadata
- Know attributes of a file - name, size, permissions, ownership, access time, etc
- Can view metadata for files with `ls -l` command, the `-l` option for long-form
- When viewing a file metadata this way, the first character indicates the file type 

|Character|Type|
|-|-|
|l|Symbolic Link|
|n|Network File|
|p|FIFO (pipe)|
|s|Socket|

```bash
-rw-rw-r-- 1 michael michael 2533 Feb 26 18:10 files.md
-rw-rw-r-- 1 michael michael  424 Feb 26 18:54 getting-information-on-files.md
```

- Above is the output of `ls -l`
- from left to right, you see file type, permissions, owner, group, number of inodes, file size in bytes (use the `-h` option for human readable file sizes), last modified data/time, file name
- inodes stores file metadata and a pointer to the data blocks on disk
- inodes don't store file names, directory inodes store file names and file inode numbers
- [YouTube video on inodes](https://youtu.be/6KjMlm8hhFA)
- view hidden files with the `-a` option 
- in Linux, file are hidden if they start with `.`
- To see file type, use the command `file [path to file]`
- The `file` command doesn't read file extensions, it reads the actual data of the file so renaming a jpeg to a txt file for instance won't make a difference
- use the `stat [file]` command to view metadata on a file in more detail 

## About extended attributes
- If the OS supports it files can have extended attributes - most OSes support this 
- extensions to normal attributes, stored on disk 
- Three major types 
  - System
    - Store access control lists (ACLs) 
    - additional layer of discretary access control 
    - access to the file is at discretion of owner, set by owner 
    - permissions can be set for multiple users and groups 
    - Provide inheritance for directories 
    - Backup and restore permissions easily
  - Security 
    - SELinux mandatory access control system
      - Layered over discretionary access control 
      - system-wide rules restricting all users including root 
      - SELinux modes 
        - Multi-level security that mimicks gov't security levels 
        - Role-based access control 
        - Type enforcement - all files, processes and users tagged with a type, permissions set on the basis of types 
  - User 
    - Store additional flags on files aptly named extended attributes 
    - flags like "append only", "compress", "immutable", "backup"

### Getting extended attributes

|Task|Command|
|-|-|
|Verify existence of ACL|`ls -l`|
|Show ACL information|`getfacl`|
|Show SELinux security context|`-Z` option|
|Show extended attributes|`lsattr`|

- Use `setfacl -m user:[user]:[permission] file` to set an access control list 
- Use `getfacl -t` to get access control list on a file
- To see SELinux security context use `ls -Z file`
- To add a user attribute run `sudo chattr +[flag] file`
- To see user attributes on a file run `lsattr -l file`

[Previous](files.md)|[Next](file-globs.md)