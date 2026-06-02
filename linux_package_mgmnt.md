# Linux Package Management

[Back to README](README.md)

- Package management refers to the ability to install packages (or applications).  
- Packages can also contain libraries.
- apt is specific to Debian / Ubuntu based.  
- Each distro has its own package manager app.

**Sub-headings**:

- [Updating Packages](#updating-packages)

## Updating Packages

[(top)](#linux-package-management)

| command | action |
| ----- | ----- |
| `sudo apt update` | update the local package index is synchronized with the package server. |
| `sudo apt install [package_name]` | installs, or checks for newer version of a package. e.g. sudo apt install vim-nox |
| `sudo apt remove [package_name]` | removes a package. may require confirmation. |
| `sudo apt autoremove` | cleans up any unnecessary packages that might have been leftover from other uninstalls. |
| `sudo apt upgrade` | installs the upgraded packages identified earlier via the apt update command. |
| `sudo apt dist-upgrade` | will also remove any packages that needed to be removed - as identified in the upgrade command. |
| `sudo reboot` | reboot and take advantage of any security updates |

[(top)](#linux-package-management)
