# Linux Command Line
<div style="text-align: left; font-size: small;">

[Back to README](README.md)

</div>

<br>

Sub-headings:
- [Basics](#basics)
- [Directories](#directories)
- [Editors](#editors)
- [Files](#files)
- [Other useful](#other-useful)
- [Changing Default Shell](#changing-default-shell)
- [Reload Shell and Source Config Changes](#reload-shell-and-source-config-changes)
- [Replace the Shell Process](#replace-the-shell-process)

<br>

## Basics 
([top](#linux-command-line))

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
| command -v [app name] | check if an app is installed. e,g, command -v vim |
| pwd | print working directory |
| whoami | who is the current user |

<br><br>

## Directories
([top](#linux-command-line))

| command | action |
| ----- | -----|
| . | current directory |
| .. | up one directory |
| mkdir [directory name] | make directory |
| cp -r [directory] [destination] | copy folder and it's contents (-r = recursive)
| mv [File or Directory] [destination] | move file or folder to [destination] |
| rmdir [directory name] | remove empty directory |
| rm -r [directory name] | remove directory and it's contents (-r = recursive) |

<br><br>

## Editors
([top](#linux-command-line))

| command | action |
| ----- | -----|
| nano | open nano text editor - simple |
| vim | open vim text editor - more complex |

<br><br>

## Files
([top](#linux-command-line))

| command | action |
| ----- | -----|
| cp [file] [destination] | copy [file] to [destination]  |
| cp [\*.\*] [destination] | copy [all files matching wildcard - i.e. containing "."] to [destination] |
| diff [file 1] [file 2] | show differences between file content |
| mv [File or Directory] [destination] | move file or folder to [destination] |
| mv [existing file name] [new filename] | rename a file |
| rm [file] | remove file |
| rm -i [file] | remove file with prompt first |
| rm [file1] [file2] | remove multiple specified files |
| rm [\*.jpg] | remove all files matching the wildcard \*.jpg |

<br><br>

## Other useful
([top](#linux-command-line))

| command | action |
| ----- | -----|
| lsblk | list block devices - i.e. shows mounting path |
| unzip [zip file name] | unzip a zip file |
| [command] --help | find help on a given command |
| exit | closes the terminal window |

<br><br>

## Changing Default Shell
([top](#linux-command-line))

| command | action |
| ----- | -----|
| echo $0 | List the current shell executable |
| cat /etc/shells | View the available shells |
| which bash or which zsh | Find the shell path  E.g. /usr/bin/bash |
| chsh -s /path/to/shell | Change the shell. E.g. chsh -s /usr/bin/bash |
| log out / in | Exit and relaunch |

<br><br>

## Reload Shell and Source Config Changes
([top](#linux-command-line))

Applies config changes without closing your current session.
| command | action |
| ----- | -----|
| For *bash*: source ~/.bashrc | Reload bash and apply config changes |
| For *zsh*: source ~/.zshrc | Reload zsh and apply config changes |

<br><br>

## Replace the Shell Process
([top](#linux-command-line))

Completely restarts the shell, clear temp variables and ensures all config is loaded fresh.
| command | action |
| ----- | -----|
| For **bash**: exec bash | Restart bash and apply config changes |
| For **zsh**: exec zsh | Restart zsh and apply config changes |

<br><br>
