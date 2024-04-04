# Git

```shell
# Git version
git --version

# Geting help
git help

# Getting help about specified command
git commit help
```

## Configuration

```shell
# list of all settings
git config --list
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

Command `git config` allows you to view and set config parameters. These parameters can
be stored in three places:

- File `/etc/gitconfig` stores values which are shared for all users and repositories
