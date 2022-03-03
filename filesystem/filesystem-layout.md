# Filesystem Layout 
- [Filesystem Hierarchy Standard - Linux Journal](https://www.linuxjournal.com/content/filesystem-hierarchy-standard)
- You can also read about the filesystem hierarchy with the command `man hier`
- Root level view of filesystem hierarchy: 

```bash
# my filesystem

.
├── bin -> usr/bin
├── boot
├── cdrom
├── dev
├── etc
├── home
├── lib -> usr/lib
├── lib32 -> usr/lib32
├── lib64 -> usr/lib64
├── libx32 -> usr/libx32
├── lost+found
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin -> usr/sbin
├── snap
├── srv
├── swapfile
├── sys
├── tmp
├── usr
└── var
```

## Overview 
- Conventions for where to put certain things that are helpful and should be used 
- root `/` is the top of the hierarchy 
- `/bin`
  - binary executables essential for booting the system
  - base operating system commands in Unix-like systems 
  - in Linux, it also contains binaries for GNU Coreutils
  - also contains links to binaries for non-fundamental software, stuff you installed
- `/sbin` 
  - System binaries
  - Critical files the operating system needs 
- `/boot`
  - Linux kernel 
  - bootloader
  - `grub`
- `/dev`
  - all devices on the system 
  - virtual devices and real devices
  - hard drives are listed as `sda` through `sdz` 
  - other types of drives can have other names
  - `/dev/shm` - files that exist in RAM only, never touching the disk 
    - Hackers like to put files here 
    - Good for storing sensitive information and temporary files 
    - Make sure files here have appropriate permissions so they can't be read or written to by malicious agents (rw---, 600)
- `/etc`
  - system configuration files 
  - configuration files for user installed software
- `/home`
  - home for all users that aren't root 
  - user files 
- `/lib`, `/lib32`, `libx32`, & `/lib64`
  - [Difference between lib, lib32, lib64, libx32, and libexec](https://unix.stackexchange.com/questions/74646/difference-between-lib-lib32-lib64-libx32-and-libexec)
  - Similar to DLLs (dynamic linked libraries) on Windows
  - Libraries that programs on the system can use 
- `/media`
  - Where auto-mounted filesystems show up (cdroms, usbs, etc)
- `/mnt`    
  - Where the user can manually mount external filesystems 
- `/opt`
  - A directory where you can install optional software that isn't installed through a package manager
  - Manually compile and install software, make a link in `/bin` to the executable in `/opt`
- `/proc`
  - numbered directories representing current processes 
    - each process directory contains a bunch of information about a process from the kernel
  - A virtual filesystem the kernel uses to communicate with you and software about the state of processes running
- `/root` 
  - root user home folder 
- `/tmp`
  - Temporary files 
  - Wiped every time you reboot 
  - ie. Unfinished download files
- `/usr` 
  - Unix source repository/Unix system resources 
  - read-only 
  - non-essential software 
  - most software on the system 
  - `/usr/local` - your own custom-written software/scripts
  - `/usr/sbin` - sys admin commands
  - `/usr/share` - stuff common to all systems
- `/var` 
  - Various 
  - Writable 
  - `/var/log` - system logs 