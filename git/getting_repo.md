# Getting Git repository

You typically obtain a Git repository in one of two ways:

1. Take a local repository that is currently nt under version control, and turn it into
a Git repository.
2. Clone an existing Git repository from elsewhere

## Initializing a repository in an existing directory

```shell
cd /home/user/my_progect
git init
```

This creates a new subdirectory named `.git` that contains all of your necessary
repository files - a Git repository skeleton.
