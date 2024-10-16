# The environment

## Environment variables

The shell maintains a set of information during a shell session, known as __the
environment__. It's just a series of key-value pairs that define properties like:

- your home directory;
- your working directory;
- the name of your shell;
- the name of the logged-in user;

and these differ from one session to the next.

These key-value pairs known as the __environment variables__.

Use [printenv](/linux/terminal/commands/printenv.md) to print the environment variables.

The names of these variables are case-sensitive.

To set environment variable use [export](/linux/terminal/commands/export.md) command.

Environment variables are kind of like global variables for shell session. They will be
accessible in all child shell sessions and in each child processes and other commands.

### Common used environment variables

- `USER` - the name of the current user;
- `HOME` - current user's home directory;
- `PWD` - stores current working directory;
- `OLDPWD` - previous location;
- [PS1](environment_variables/ps1.md) - variable that governs prompt;

## Shell variables

To define a __shell variable__, use the syntax `variable=value`.

Built-in variables are upper-cased, so it's a common convention to lowercase custom
variables to prevent confusion.

```shell
color=purple
echo $color
# purple
```

You can use quotes if you value contain spaces.

```shell
name="James Smith"
```

```shell
num=737
echo $num
# 737
```

We defined shell variables. They are not environment variables. If we type
`printenv color` we will see nothing.

Shell variables are kind of like local variables. They only exist in our current shell
session.

But it is not difficult to make our shell variable an environment variable, using
`export` command:

```shell
# this is shell variable
color=purple

# now it turns to environment variable
export color
```

Set a new value to existing variable:

```shell
# create variable
color=purple
# set a new value
color=red
```

## Startup files

There are multiple files on our machine that are very particular files that bash looks
for. The shell will look to and read information from. They include configuration
details, instructions, predefined variables and functions, just a bunch of config stuff.

When we log in, the shell reads information from startup files. First, the shell reads
from global config files that effects the environment for all users. Then, the shell
reads startup files for specific users.

`etc/bash.bashrc` - global config for all users

The specific files the shell reads from depends on the type of session: login or
non-login shell sessions.

For non-login sessions (typical session when you launch the terminal via the GUI):
`~/.bashrc` - specific settings for each user. This is where we can define our own
settings and configuration.

For login sessions:

- `/etc/profile` - global config for all users;
- `~/.bash_profile` - user's personal config file;
- `~/.bash_login` - read if bash_profile isn't found;
- `~/.profile` - used if previous two aren't found;
