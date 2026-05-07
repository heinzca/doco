<div style="text-align: left; font-size: small;">

[Back to README](README.md)

</div>

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

<br><br>

## Directories
| command | action |
| ----- | -----|
| mkdir [directory name] | make directory |
| cp -r [directory] [destination] | copy folder and it's contents (-r = recursive)
| mv [File or Directory] [destination] | move file or folder to [destination] |
| rmdir [directory name] | remove empty directory |
| rm -r [directory name] | remove directory and it's contents (-r = recursive) |

<br><br>

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

<br><br>

## Other useful
| command | action |
| ----- | -----|
| lsblk | list block devices - i.e. shows mounting path |
| unzip [zip file name] | unzip a zip file |
| [command] --help | find help on a given command |
| exit | closes the terminal window |

<br><br>

## Changing Default Shell
| command | action |
| ----- | -----|
| echo $0 | List the current shell executable |
| cat etc/shells | View the available shells |
| which bash or which zsh | Find the shell path  E.g. /usr/bin/bash |
| chsh -s /path/to/shell | Change the shell. E.g. chsh -s /usr/bin/bash |
| log out / in | Exit and relaunch |

<br><br>

## Reload Shell and Source Config Changes
Applies config changes without closing your current session.
| command | action |
| ----- | -----|
| For *bash*: source ~/.bashrc | Reload bash and apply config changes |
| For *zsh*: source ~/.zshrc | Reload zsh and apply config changes |

<br><br>

## Replace the Shell Process
Completely restarts the shell, clear temp variables and ensures all config is loaded fresh.
| command | action |
| ----- | -----|
| For **bash**: exec bash | Restart bash and apply config changes |
| For **zsh**: exec zsh | Restart zsh and apply config changes |

<br><br>