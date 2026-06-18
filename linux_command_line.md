# Linux Command Line

[Back to README](README.md)

Sub-headings:

- [Basics](#basics)
- [Directories](#directories)
- [Editors](#editors)
- [Files](#files)
- [History](#history)
- [Other useful](#other-useful)
- [Output Re-direction](#output-re-direction)
- [Streams](#streams)
- [Find](#find)

## Basics

([top](#linux-command-line))

| command | action |
| ----- | ----- |
| `ls` | list (list storage) |
| `ls -l` | list - long format |
| `ls -la` | list all (including hidden files) - long format |
| `cd [directory path]` | change directory |
| `cd` | change to home  directory |
| `cd ~` | change to home  directory |
| `cd /` | change to root directory |
| `cd ..` | move up one directory |
| `cd ../..` | move up multiple directories - keep repeating |
| `clear` | clear window |
| `command -v [app name]` | check if an app is installed. e,g, command -v vim |
| `echo "this text"` | print the content in quotes to screen |
| `echo $?` | print the exit code of the last command - see [streams](#streams) |
| `pwd` | print working directory |
| `whoami` | who is the current user |

## Directories

([top](#linux-command-line))

| command | action |
| ----- | ----- |
| `.` | current directory |
| `..` | up one directory |
| `mkdir [directory name]` | make directory |
| `cp -r [directory] [destination]` | copy folder and it's contents (`-r` = recursive) |
| `mv [File or Directory] [destination]` | move file or folder to 'destination' |
| `rmdir [directory name]` | remove empty directory |
| `rm -r [directory name]` | remove directory and it's contents (`-r` = recursive) |

## Editors

([top](#linux-command-line))

| command | action |
| ----- | ----- |
| `nano` | open nano text editor - simple |
| `vim` | open vim text editor - more complex |

## Files

([top](#linux-command-line))

| command | action |
| ----- | ----- |
| `cp [file] [destination]` | copy 'file' to 'destination' |
| `cp [\*.\*] [destination]` | copy all files matching wildcard - i.e. containing "." to 'destination' |
| `diff [file 1] [file 2]` | show differences between file content |
| `mv [File or Directory] [destination]` | move file or folder to 'destination' |
| `mv [existing file name] [new filename]` | rename a file |
| `rm [file]` | remove file |
| `rm -i [file]` | remove file with prompt first |
| `rm [file1] [file2]` | remove multiple specified files |
| `rm [\*.jpg]` | remove all files matching the wildcard \*.jpg |

## History

([top](#linux-command-line))

| command | action |
| ----- | ----- |
| `history` | display a history list of commands |
| `h` | history (aliased to h) |
| `!!` | re-execute your last command |
| `sudo !!` | this will enable you to run a previous command as sudo if you forgot the sudo first time |
| `![nnn]` | execute a history entry = nnn  (e.g. !745) |
| `[space][command]` | adding a space to the start of a command will stop it appearing in history. |
| `history [n]` | displays the last n commands (alias e.g. h 10) |
| `history \| grep [search text]` | search for a command with given text |

## Other useful

([top](#linux-command-line))

| command | action |
| ----- | ----- |
| `lsblk` | list block devices - i.e. shows mounting path |
| `unzip [zip file name]` | unzip a zip file |
| `[command] --help` | find help on a given command |
| `exit` | closes the terminal window |

## Output Re-direction

([top](#linux-command-line))

You can re-direct the output of a given command into a file.

There are a few ways this can be done.

### New file re-direction

Use the `>` symbol to re-direct the output to a new file:

- `ls -l > newfile1.txt`

**Key points here**:

- If the defined file doesn't already exist, it will be created.
- If the file does already exist, then it will be over-written by the latest execution of the command.
- ***Be careful with a single `>`*** as it will blow away any existing content in the original file if you over-write,

### Append re-direction to a file

Use `>>` to re-direct the output and append to a file if it exists:

- `ls -l >> newfile2.txt`

**Key points here**:

- Again, if the defined file doesn't already exist, it will be created.
- However, if the file does already exist, then the re-directed output will be appended to the end of the existing file.

### Re-direct to 'purgatory'

- If you want to 'cast aside' content from a command, you can write it to a specific path as follows:
  - /dev/null
- anything written there 'disappears'.
  - No file is written.
  - No remnants are left.
  - It is just 'sent to purgatory'.
  - Anything written here is not seen nor heard from again.
- Can be useful to filter out stderr (standard errors) via exit code 2.
  - see [filter out stderr example](#filter-out-stderr-example).

### Chaining (or piping) commands

This enable you to 'pipe' the output of one command as input into the next command and so on.

You use the pipe symbol `|` to do this.

This can be very powerful.

**Examples**:

| command | action |
| ----- | ----- |
| `ls -l \| grep f` | This runs the output of the `ls -l` through the `grep f`, effectively searching for only records which contain the letter f. |
| `cat file2.txt \| sort \| uniq \| grep -v txt` | This example takes the contents of a given file, sorts them, then identifies the unique records, then excludes (via `grep -v`) any files containing the text txt. |
| `ls -l \| wc` | This pipes the output into `wc` (word count) which gives you three outputs: rows, words, characters as output. |
| `ls -l \| wc -l` | This pipes the output into `wc -l` (word count -> lines option) which gives you a row count as output. |
| `ls -l /etc \| wc -l` | Example to get the count of lines in a given specified directory - i.e. /etc. |

## Streams

([top](#linux-command-line))

There are three different 'streams' in Linux:

1. stdin - standard input (file descriptor: 0)
2. stdout - standard output (file descriptor: 1)
3. stderr - standard error (file descriptor: 2)

### Standard Input - stdin

- Standard Input is effectively anything that is input into a command.
- This could be input from the keyboard, or output from a previous command, which is then redirected or piped into another command as input.

### Standard Output - stdout

- This is any successful output that **has not** resulted in an error.
- This basically means when we have received output that is valid, it is standard output.
- to write all stderr from a find command to a file, you could use this:
  - `find / -name *.log 1> successful.txt`

### Standard Error - stderr

- This is output that **has** resulted in an error.
- This output is defined as standard error.
- to write all stderr from a find command to a file, you could use this:
  - `find / -name *.log 2> errors.txt`
  
#### Filter out stderr example

- a useful example of filtering out / removing stderr content is as follows:
  - `find / -name *.log 2> /dev/null`
  - in this example we find all log files in the root directory but re-direct stderr (2) into `/dev/null` via the `2> /dev/null`
  - see [redirect to purgatory](#re-direct-to-purgatory) for more detail.

### echo command

- You can check the exit code for the previous command via:
  - `echo $?`
- Run this after
  - a successful command like: `ls`, you should see 0 returned.
  - trying to cd into a non-existent directory, (like `ls turtles`), you should see 2 returned.
- `$?` is actually a special variable that defines the exit code of the previous command.
  - So echoing that out returns 0 (stdin) or 2 (stderr).

## find

The find command is very useful for hunting down files or directories.

Example:

- `find /var/log/ -type f -name "*.log" -mtime -7`
  - `/var/log` defines the directory to search in
  - `-type f` defines type = file
  - `-name "*.log"` searches by name using wildcard
  - `-mtime -7` defines modified in the last 7 days

Another example - filtering out errors to /dev/null:

- `find /var -type f -name "*log" 2> /dev/null`
  - `2> /dev/null` in this case discards errors (like files I don't have access permissions on).

You can also use `-exec` to execute a command on the results fo what you have found. BUT, be careful as this can create issues if you execute something incorrectly.
