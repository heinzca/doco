# Manage systemd Units

[Back to README](README.md)

systemd refers to the processes running on your machine

**Sub-headings**:

- [systemctl - system control](#systemctl---system-control)

## systemctl - system control

| command | action |
| ---------- | ---------- |
| `systemctl status [package_name]` | shows what the defaut status is, current status, as well as other basic info. e.g. `systemctl status apache2` |
| `sudo systemctl disable [package_name]` | sudo required here to disable. will change it from enabled to disabled, so it won't start by default when machine starts. (Doesn't stop an existing running service.) |
| `sudo systemctl stop [package_name]` | stops a running package |
| `sudo systemctl enable [package_name]` | enable a specific package that was disabled. e.g. `sudo systemctl enable apache2` |
| `sudo systemctl start [package_name]` | start a process that wasn't previously running |
| `sudo systemctl restart [package_name]` | re-start a process that was previously running - but needs a reboot |
