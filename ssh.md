# ssh - OpenSSH

[Back to README](README.md)

ssh (OpenSSH) enables you to log into a remote instance.

**Sub-headings:**

* [ssh client](#ssh-client)
* [ssh server](#ssh-server)
* [net-tools](#net-tools)
* [Connect to a server](#connecting-to-a-server)
* [Disallow root access](#disallow-root-access)
* [Disallow password authentication](#disallow-password-authentication)

## ssh client

The OpenSSH client (ssh) is installed by default on most Linux machines.

| command | action |
| ----- | ----- |
| `which ssh` | checks if the ssh client is installed. if it is, the path will be displayed. |
| `man ssh` | opens the manual for ssh. |

[(top)](#ssh---openssh)

## ssh server

To be able to connect **to** a machine you need to have the ssh server installed on the target machine. You may need '[net-tools](#net-tools)' to check some of this -> see below.

A few ways to check of you have the server installed:

1. run `sudo netstat -tulpn` -> if 'sshd' is running it would show in the PID/Program Name.
2. run `which sshd` -> if installed you will see the path.
3. `systemctl status ssh` -> shows you if it is running / installed.

If it's not installed on Debian/Ubuntu, you can install it via:  

* `sudo apt install openssh-server`

[(top)](#ssh---openssh)

## net-tools

There is a package of networking tools called net-tools which is now deprecated and has been replaced by more modern tools, however it is still very useful.

To install use:

* `sudo apt install net-tools`

Includes:

| net-tools | modern tool |
| ----- | ----- |
| arp | ip neigh |
| ifconfig | ip addr |
| ipmaddr | ip maddr |
| iptunnel | ip tunnel |
| route | ip route |
| nameif | ifrename |
| mii-tool | ethtool |

[(top)](#ssh---openssh)

## Connecting to a Server

| command | action |
| ----- | ----- |
| `ssh [user]@[IP address]` | e.g. `ssh hca@172.105.29.169` this will then prompt for a password, assuming no private key requirement |
| `ssh [IP address]` | you can connect directly to an IP address if your current user name matches the user name on that remote IP. e.g. `ssh 172.105.29.169` in this case, there is no need to define the user. |
| `ssh -i "my_key.pem" user@ec2-18.136.143.214.ap-southeast-2.compute.amazonaws.com` | AWS example using `-i` for "identity-file" - such as a private key. define the private key file after `-i`, then supply the full user@url address. in this case, make sure your private key is not publicly viewable via: `chmod 400 "my_key.pem"` |
| `ssh -p 2222 jay@172.105.29.169` | example defining a specific port number - if the instance is listening on a non-default port. this can be done to add reduce the 'fishing' for new instances. |

Safety Guidelines:

* [Disallow root access](#disallow-root-access)
* [Disallow password access](#disallow-password-authentication)
* Authenticate via SSH keys instead (not covered yet)

[(top)](#ssh---openssh)

## Disallow root access

To disallow root access:

1. Firstly, create a separate user who has sudo access. To check this run `sudo -l` - which shows what you can do (ALL - is everything!)
2. Edit the following file (va nano):
`/etc/ssh/sshd_config`
3. Update the setting 'PermitRootLogin' to no
4. Then restart ssh via: `sudo systemctl restart ssh`
5. Any attempts to log in directly as user: 'root' will come back as permission denied

[(top)](#ssh---openssh)

## Disallow password authentication

1. Again within the 'sshd_config' file.
2. Update the setting 'PasswordAuthentication' to no.
3. **Danger here**: you will not be able to log in all attempts will come back with permission denied.
4. You should only do this once you have set up / enabled 'public key authentication'. (*It looks like AWS does this by default.*)

[(top)](#ssh---openssh)
