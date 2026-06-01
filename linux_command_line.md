# Linux Command Line

[Back to README](README.md)

Sub-headings:

- [Basics](#basics)
- [Directories](#directories)
- [Editors](#editors)
- [Files](#files)
- [History](#history)
- [Other useful](#other-useful)

## Basics

([top](#linux-command-line))

| command | action |
| ----- | ----- |
| `ls` | list (list storage) |
| `ls -l` | list - long format |
| `ls -la` | list all (including hidden files) - long format |
| `cd [directory path]` | change directory |
| `cd` | change to home  directory |
| `cd ~` | change to home  directory |
| `cd /` | change to root directory |
| `cd ..` | move up one directory |
| `cd ../..` | move up multiple directories - keep repeating |
| `clear` | clear window |
| `command -v [app name]` | check if an app is installed. e,g, command -v vim |
| `pwd` | print working directory |
| `whoami` | who is the current user |

## Directories

([top](#linux-command-line))

| command | action |
| ----- | ----- |
| `.` | current directory |
| `..` | up one directory |
| `mkdir [directory name]` | make directory |
| `cp -r [directory] [destination]` | copy folder and it's contents (`-r` = recursive) |
| `mv [File or Directory] [destination]` | move file or folder to 'destination' |
| `rmdir [directory name]` | remove empty directory |
| `rm -r [directory name]` | remove directory and it's contents (`-r` = recursive) |

## Editors

([top](#linux-command-line))

| command | action |
| ----- | ----- |
| `nano` | open nano text editor - simple |
| `vim` | open vim text editor - more complex |

## Files

([top](#linux-command-line))

| command | action |
| ----- | ----- |
| `cp [file] [destination]` | copy 'file' to 'destination' |
| `cp [\*.\*] [destination]` | copy all files matching wildcard - i.e. containing "." to 'destination' |
| `diff [file 1] [file 2]` | show differences between file content |
| `mv [File or Directory] [destination]` | move file or folder to 'destination' |
| `mv [existing file name] [new filename]` | rename a file |
| `rm [file]` | remove file |
| `rm -i [file]` | remove file with prompt first |
| `rm [file1] [file2]` | remove multiple specified files |
| `rm [\*.jpg]` | remove all files matching the wildcard \*.jpg |

## History

([top](#linux-command-line))

| command | action |
| ----- | ----- |
| `history` | display a history list of commands |
| `h` | history (aliased to h) |
| `!!` | re-execute your last command |
| `sudo !!` | this will enable you to run a previous command as sudo if you forgot the sudo first time |
| `![nnn]` | execute a history entry = nnn  (e.g. !745) |
| `[space][command]` | adding a space to the start of a command will stop it appearing in history. |
| `history [n]` | displays the last n commands (alias e.g. h 10) |
| `history \| grep [search text]` | search for a command with given text |

## Other useful

([top](#linux-command-line))

| command | action |
| ----- | ----- |
| `lsblk` | list block devices - i.e. shows mounting path |
| `unzip [zip file name]` | unzip a zip file |
| `[command] --help` | find help on a given command |
| `exit` | closes the terminal window |
