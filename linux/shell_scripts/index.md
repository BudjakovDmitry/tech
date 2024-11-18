# Shell scripts

In the simplest terms, a shell script is a text file containing a series of commands.
The shell reads this file and carries out the commands as though they have been entered
directly on the command line.

## Multiple commands on a line

It's possible to put more than one command on a line by separating each command with a
semicolon.

```shell
command1; command2; command3...
```

```shell
cd /usr; lsl cd -
```

## How to write a Shell script?

To create and run a shell script, we need to do three things:

1. Write a script.
2. Make the script executable. We need to set the script file's permissions to allow
execution. Note, that scripts must be readable to be executed.
3. Put the script somewhere the shell can find it. The shell automatically searches
certain directories for executable files when no explicit path-name is specified. For
maximum convenience, we will place our scripts in these directories.

## Hello world

```shell
#!/bin/bash

# This is our first script

echo 'Hello World!' # prints Hello World!
```

Everything from the `#` symbol onward on the line is ignored.

The `#!` character sequence is a special construct called *shebang*. The shebang is used
to tell the kernel the name of the interpreter that should be used to execute the
script. Every shell script should include this as its first line.
