# Shells
<div style="text-align: left; font-size: small;">

[Back to README](README.md)

</div>

<br>

Sub-headings:
- [Changing Default Shell](#changing-default-shell)
- [Reload Shell](#reload-shell-and-source-config-changes)
- [Replace the Shell](#replace-the-shell-process)

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