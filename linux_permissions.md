# Linux Permissions
<div style="text-align: left; font-size: small;">

[Back to README](README.md)

</div>

<br>

Sub-headings:
- [Permissions 101](#permissions-101)
- [chmod](#chmod)

<br><br>

## Permissions 101
[(top)](#linux-permissions)

The permissions for a given directory or file are displayed in 'long' view when you ls -l.  
The 10-characters make up four distinct sets of info:
1. Single character (char 1) which defines the 'type' as either a:
    * "d" as a directory
    * "-" as a file
    * "l" as a link
2. Three characters defining the permissions for the owner of the item:
    * "r" defining read
    * "w" defining write
    * "x" defining execute
    * Where "-" is shown, that permission does not apply.
    * e.g. 
        * "rwx" means you have read, write, execute
        * "r-x" means you have read, execute, but no write
        * "---" means no access
3. Three characters defining the permissions for the group listed for the item:
    * Again using the rwx approach
4. Three characters defining the permissions for all other users:
    * Again using the rwx approach


**Sample:** drwxrwxr-x  

Defines:

1. A directory
2. owner has read, write, execute
3. group has read, write, execute
4. other users have read, execute only, no write

Directory Permissions:
- r = able to see contents
- w = able to change contents
- x = able to enter into directory

File permissions:
- r = able to see contents
- w = able to change contents
- x = able to execute a script


<br><br>

## chmod
[(top)](#linux-permissions)

| command | action |
| ----- | -----|
| chmod +x [filename] | give x (execute) to all users - no user/group defined|
| chmod -x [filename] | remove x (execute) from all users - no user/group defined |
| chmod u+x [filename] | give x (execute) to user (u) only |
| chmod a+rwx [filename] | give everybody (a = all) full access |
| chmod g-rwx [filename] | remove rwx from the group (g) |
| chmod o-rwx [filename] | remove rwx from the other users group (o) |

In summary
* u = user
* g = group
* o = other users
* a = all

<br><br>
[(top)](#linux-permissions)