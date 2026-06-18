# Linux Package Management

[Back to README](README.md)

- Package management refers to the ability to install packages (or applications).  
- Packages can also contain libraries.
- apt is specific to Debian / Ubuntu based.  
- Each distro has its own package manager app.

**Sub-headings**:

- [Updating Packages](#updating-packages)
  - [Debian-based Distros](#debian-based-distros)
  - [CentOS Distro](#centos-distro)
  - [Fedora Distros](#fedora-distros)

## Updating Packages

[(top)](#linux-package-management)

### Debian-based Distros

[(top)](#linux-package-management)

Debian-based distros (which includes Ubuntu) use the apt package manager:

| command | action |
| ----- | ----- |
| `sudo apt update` | update the local package index is synchronized with the package server. |
| `sudo apt install [package_name]` | installs, or checks for newer version of a package. e.g. sudo apt install vim-nox |
| `sudo apt remove [package_name]` | removes a package. may require confirmation. |
| `sudo apt autoremove` | cleans up any unnecessary packages that might have been leftover from other uninstalls. |
| `sudo apt upgrade` | installs the upgraded packages identified earlier via the apt update command. |
| `sudo apt dist-upgrade` | will also remove any packages that needed to be removed - as identified in the upgrade command. |
| `sudo reboot` | reboot and take advantage of any security updates |

### CentOS Distro

[(top)](#linux-package-management)

CentOS uses the yum package manager.

Similar to apt.

Check the yum man page if required.

### Fedora Distros

[(top)](#linux-package-management)

Fedora-based distros use the dnf package manager.

Fedora uses dnf, which is a replacement for the yum package manager.

Commands are similar to apt, but using dnf in place of apt.

Again check the dnf man page as required.
