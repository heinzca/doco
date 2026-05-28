# Shells
<div style="text-align: left; font-size: small;">

[Back to README](README.md)

</div>

<br>

Sub-headings:
- [Bash](#bash)
    - [.bashrc](#bashrc)
    - [aliases](#aliases)
- [Changing Default Shell](#changing-default-shell)
- [Reload Shell](#reload-shell-and-source-config-changes)
- [Replace the Shell](#replace-the-shell-process)

<br><br>

## Bash
([top](#shells))

### .bashrc

Configuration of bash is via the .bashrc file, which lives in your: ~/

**Note:**
* The template for .bashrc lives in the following directory: /etc/skel/.bashrc
* When a new user is created, the .bashrc file they receive is a copy of that template.

### aliases

Aliases are shortcuts to execute a onger command.  
They are generally defined within the .bashrc file.  
They can also be put into a separate .bash_aliases file.  


| command | action |
| ----- | -----|
| alias | list out all of the aliases in your config |
| unalias [alias name] | temporarily stop an alias until the next terminal launch |

<br><br>

## Changing Default Shell
([top](#shells))

| command | action |
| ----- | -----|
| echo $0 | List the current shell executable |
| cat etc/shells | View the available shells |
| which bash or which zsh | Find the shell path  E.g. /usr/bin/bash |
| chsh -s /path/to/shell | Change the shell. E.g. chsh -s /usr/bin/bash |
| log out / in | Exit and relaunch |

<br><br>

## Reload Shell and Source Config Changes
([top](#shells))

Applies config changes without closing your current session.
| command | action |
| ----- | -----|
| For *bash*: source ~/.bashrc | Reload bash and apply config changes |
| For *zsh*: source ~/.zshrc | Reload zsh and apply config changes |

<br><br>

## Replace the Shell Process
([top](#shells))

Completely restarts the shell, clear temp variables and ensures all config is loaded fresh.
| command | action |
| ----- | -----|
| For **bash**: exec bash | Restart bash and apply config changes |
| For **zsh**: exec zsh | Restart zsh and apply config changes |

<br><br>
