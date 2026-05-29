# Linux Resource Monitoring
<div style="text-align: left; font-size: small;">

[Back to README](README.md)

</div>

<br>

Sub-headings:
- [free - check ram]()
- [df - check disk space]()


## free - check ram
[(top)](#linux-resource-monitoring)  

The free command allows you to check ram usage.

| command | action |
| ----- | -----|
| free | shows used, free vailable in kb |
| free -m | shows used, free vailable in mb |

<br><br>

## df - check disk space
[(top)](#linux-resource-monitoring)  

| command | action |
| ----- | -----|
| df -h | shows used / available disk spacein human readable format |
| df -i | shows inode usage / free (monitor IUse%) |


## htop - utility to show processes
[(top)](#linux-resource-monitoring)  

| command | action |
| ----- | -----|
| htop | displays a cool resource mangement tool - showing lots of stuff. |
| F9 | Can also manage / kill processes (via F9 - SIGTERM) if hung. |


## uptime
* shows system uptime, logged in users plus load average
* load average values are:
    * last minute
    * last 5 minutes
    * last 15 minutes
* Keep an eye if it's getting higher

<br><br>

[(top)](#linux-resource-monitoring)  