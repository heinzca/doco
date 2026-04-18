# Linux Command Line

## Basics

| command | action |
| ----- | -----|
| ls | list |
| ls -l | list - long format |
| ls -la | list all (including hidden files) - long format |
| cd [directory path]| change directory |
| cd | change to home  directory |
| cd ~ | change to home  directory |
| cd / | change to root directory |
| cd .. | move up one directory |
| cd ../.. | move up multiple directories - keep repeating |
| clear | clear window |
| pwd | print working directory |


## Directories
| command | action |
| ----- | -----|
| mkdir [directory name] | make directory |
| cp -r [directory] [destination] | copy folder and it's contents (-r = recursive)
| mv [File or Directory] [destination] | move file or folder to [destination] |
| rmdir [directory name] | remove empty directory |
| rm -r [directory name] | remove directory and it's contents (-r = recursive) |

## Files
| command | action |
| ----- | -----|
| cp [file] [destination] | copy [file] to [destination]  |
| cp [\*.\*] [destination] | copy [all files matching wildcard - i.e. containing "."] to [destination] |
| mv [File or Directory] [destination] | move file or folder to [destination] |
| rm [file] | remove file |
| rm -i [file] | remove file with prompt first |
| rm [file1] [file2] | remove multiple specified files |
| rm [\*.jpg] | remove all files matching the wildcard \*.jpg |

## Other useful
| command | action |
| ----- | -----|
| lsblk | list block devices - i.e. shows mounting path |
| unzip [zip file name] | unzip a zip file |
| [command] --help | find help on a given command |
| exit | closes the terminal window |


# sudo - SuperUser Do

Executes commands as the super user / admin.

## sudo commands

| command | action |
| ----- | -----|
| sudo reboot | quick reboot - via terminal |
| sudo shutdown now | immediate shutdown - via terminal |

## APT (Advanced packaging Tool)

**apt** is used for installing packages. More modern version of **apt-get**.

Installs applications from online repositories.

| command | action |
| ----- | -----|
| sudo apt update | sudo (superuser) update apt repository locations |
| sudo apt upgrade | sudo (superuser) upgrade updatable apt repository locations |
| sudo apt update && sudo apt upgrade | sudo (superuser) update package list and upgrade installed packages |
| sudo apt install [package name] | install an application package |
| sudo apt remove [package name] | remove an application package |



