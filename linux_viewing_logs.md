# Viewing Logs

[Back to README](README.md)

Logs generally reside in the following system directory:

* /var/log/

Some may reside in further sub-directories, but the core one is syslog (system log).

**Sub-headings:**

* [syslog](#syslog)
* [journalctl](#journalctl)

## syslog

| command | action |
| ----- | ----- |
| `cd /var/log` | open the log directory |
| `cat syslog` | shows the full content - but often too big to make any sense here. |
| `head /var/log/syslog` | head gives you the first 10 records in the file by default. If inside `/var/log/` can drop that from path. |
| `head -nn /var/log/syslog` | extend the number of head records via `-nn`. |
| `tail /var/log/syslog` | tail gives you the last 10 records in the file by default. |
| `tail -nn /var/log/syslog` | extend the number of tail records via `-nn`. |

## journalctl

| command | action |
| ----- | ----- |
| `journalctl -u [package_name]` | displays log entries for a given process. e.g. `journalctl -u apache2` |
 `journalctl -fu [package_name]` | displays log entries for a given process and follow it (see new items displayed as they occur). e.g. `journalctl -fu apache2` |
