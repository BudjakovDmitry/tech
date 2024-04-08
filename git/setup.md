# Git setup

## First-Time Git setup

Git comes with tool called `git config` that lets you get and set configuration
variables. These variables can be stored in three different places:

- `[path]/etc/gitconfig` file: contains values applied to every user on the system and
all their repositories. If you pass the option `--system` to `git config`, it reads and
writes from this file specifically. Because this is a system configuration file, you
would need administrative or superuser privilege to make changes to it.
- `~/.gitconfig` or `~/.config/git/config` file: values specific personally to the user.
You can make Git read and write to this file specifically by passing the `--global`
option, and this affects all the repositories you work with on your system.
- `config` file in the git directory (`.git/config`): specific to single repository. You
can force Git to read from and write to this file with the `--local` option, but that is
in fact the default. You need to be located somewhere in a Git repository for this
option to work properly.

Each leval overrides values in the previous level.

```shell
# list of all settings
git config --list

# view all settings and where they are coming from
git config --list --show-origin
```

```shell
# set username
git config --global user.name "John Doe"

# set email
git config --global user.email "dohn.doe@mail.com"

# view specified settings
git config user.name
git config user.email
```

