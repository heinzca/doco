# Managing Users

[Back to README](README.md)

## /etc/passwd

* You can see a list of users via: `cat /etc/passwd`
* Users with 'nologin' indicate they are unable to log-in.
* Records for real users show:
  * User ID
  * x indicates the user's password is held in a separate file
  * UID - numeric value
  * Group ID (can be same as UID)
  * Name
  * Home directory
  * Default shell
* UIDs of 1000 or higher appear on the GUI - log-in screen.
* Those below 1000 do not appear on the default log-in screen.

## /etc/shadow

* This file shows the password hash for some 'real' users (but not the actual password)
* To access it you need sudo. e.g.
  * `sudo cat /etc/shadow`
* There is broader scope, but not covered here.

## /etc/group

* You can view a list of groups via: `cat /etc/group`
* Groups can be used to grant / limit certain functionality.
* Users within a group are also listed following the last ':'

## View groups for a user

| command | action |
| ---------- | ---------- |
| `groups` | lists current user and the groups they have |
| `groups [user_id]` | lists defined user and the groups they have |

## Adding users

Only root can create users, so need to use sudo.

| command | action |
| ---------- | ---------- |
| `sudo adduser [user_name]` | creates user and will prompt for a few things: password (plus re-type to confirm), as well as optional: full name and contact details. Also creates their home directory based on defaults from /etc/skel/ |

## Switch to a user account

**Option 1:**

* `su - [user_id]`
* then prompts for password
* logout will log you out of that account

**Option 2:**

* as sudo: `sudo su - [user_id]`
* no password prompt

## Changing a password

* `passwd` - will prompt for current and new passwords (plus re-type new to confirm)
* as sudo: `sudo passwd [user_id]`
  * no prompt for existing
  * can set new password

## Log in specifically as root

* `sudo su -`
* `passwd [user_id]`
* logout (of root) when done via:
  * `logout`
  * `exit`
  * `ctrl + d`

## Remove a user

| command | action |
| ---------- | ---------- |
| `sudo userdel -r [user_id]` | delete user and remove all files. To retain files after killing the user, leave out the `-r` |

## Create a group

* `sudo groupadd [group_name]`
* view group via `cat /etc/group`

## Add user to a group

* via: `sudo usermod -aG [group_name] [user_id]`
* user then needs to log out and back in to see new group addition
* can check via `groups [user_id]`

## Remove user from a group

* `sudo gpasswd -d [user_id] [group_id]`
* can check via `groups [user_id]`

## Remove a group completely

* via: `sudo groupdel [group_name]`
* check via `cat /etc/group` or `tail /etc/group`
