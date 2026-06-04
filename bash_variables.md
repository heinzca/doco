# Bash Variables

[Back to README](README.md)

## Creating Session Variables

You can create a 'session variable' (*only applies to the current Bash session*) by declaring it as follows:

- `HELLOMSG="Hello World"`
- You can print it back via echo as follows:
  - `echo $HELLOMSG`

**Notes**:

- Variables are generally declared as `ALLCAPS` but it is not critical.
- You need to use `$` to access the variable in the output.

An example of using a variable within text:

- `MYNAME="Beanz"`
- `echo "My name is $MYNAME"`

Another example using a path in a variable:

- `MY_DIR="/home/hca/dev"`
- `echo $MY_DIR`
- `ls -l $MY_DIR`

(This may not be practical, unless you are using a very specific longer path for a given purpose.)

## Persistent variables

To make variables persistent (*beyond the current session*) you can declare them in your .bashrc file.

This would make them available in any bash session you open.

## Environment Variables

To view a list of your environment variables, you can use the command:

- `env`

**Note**:

- session variables do not appear under `env` output.
- to add an environment variable you need to add it using `export` as follows:
  - `export MYVAR="linux"`
- you should then see it in the `env` list.
