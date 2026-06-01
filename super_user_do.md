# sudo - SuperUser Do

[Back to README](README.md)

`sudo` executes commands as the super user / admin.  

Sub-headings:

- [sudo commands](#sudo-commands)
- [APT (Advanced packaging Tool)](#apt-advanced-packaging-tool)

## sudo commands

([top](#sudo---superuser-do))

| command | action |
| ----- | ----- |
| `sudo reboot` | quick reboot - via terminal |
| `sudo shutdown now` | immediate shutdown - via terminal |

## APT (Advanced packaging Tool)

([top](#sudo---superuser-do))

**apt** is used for installing packages. More modern version of **apt-get**.

Installs applications from online repositories.

| command | action |
| ----- | ----- |
| `sudo apt update` | sudo (superuser) update apt repository locations |
| `sudo apt upgrade` | sudo (superuser) upgrade updatable apt repository locations |
| `sudo apt update && sudo apt upgrade` | sudo (superuser) update package list and upgrade installed packages |
| `sudo apt install [package_name]` | install an application package |
| `sudo apt remove [package_name]` | remove an application package |
