# Linux Package Management
<div style="text-align: left; font-size: small;">

[Back to README](README.md)

</div>

Package mangement refers to the ability to install packages (or applications).  

Packages can also contain libraries.

apt is specific to Debian / Ubuntu based.  

Each distro has its own package manager app.

<br>

Sub-headings:
- [Updating Packages](#updating-packages)

<br><br>

## Updating Packages
[(top)](#linux-package-management)

| command | action |
| ---------- | -----|
| sudo apt update | update the local package index is synchronised with the package server. |
| sudo apt install [package_name] | installs, or checks for newer version of a package. e.g. sudo apt install vim-nox |
| sudo apt remove [package_name] | removes a package. may require confirmation. |
| sudo apt autoremove | cleans up any unnecessary packeges that might have been leftover from other uninstalls. |
| sudo apt upgrade | installs the upgraded packages identified earlier via the apt update command. |
| sudo apt dist-upgrade | will also remove any packages that needed to be removed - as identified in the upgrade command. |
| sudo reboot | reboot and take advantage of any security updates |

<br><br>

[(top)](#linux-package-management)