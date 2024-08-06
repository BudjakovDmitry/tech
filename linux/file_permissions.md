# File permissions and ownership

For managing files and directory permissions use [chmod](terminal/commands/chmod.md)
command.

Linux is a multi-user operating system. This means that by default, other users will be
able to view any files you store on the system. However, you may have some files such as
your personal tax documents or your employer's intellectual property documents - that
are private or confidential. You can protect these sensitive documents from being viewed
or modified by others.

There are three possible levels of file ownership in Linux:

- *user*;
- *group*;
- *other*.

Every file or directory has its owner. Whoever creates a file, namely the user, at the
time of creation, becomes the owner of that file by default.

Additionally, users can belong to *groups* which are given access to particular files
and folders by their owners. A group of users can also share ownership of a file. Each
file or directory has a group owner. For example, we can create a group, add users to
this group and add read permissions to a specified file. This way all group members will
be able to read the file.

The *other* category essentially refers anyone in the universe with access to your Linux
machine.

Only an official owner of a file is allowed to change its permissions. This means that
only owners can decide who can read the file, write to it, or execute it.

## Viewing file permissions

Let's say you've entered the following lines of code:

```shell
echo "Who can read this file?" > my_new_file

ls -l my_new_file
-rw-r--r-- 1 john_doe users Dec 18 09:07 my_new_file
```

Let's have a closer look on file permissions.

First `-` indicates that this is a file. Next first three characters (`rw-`) define the
*user* permissions, the next three (`r--`) the *group* permissions, and the final three
(`r--`) the *other* permissions.

- `r` read;
- `w` write;
- `x` execute;

So you, being the user, have the permission `rw-`, which means you have read and write
permissions by default, but do not have execution permissions. Otherwise, there would be
an `x` in place of the last `-`.

Thus, by looking at the entire line, `rw-r--r--`, you can see that anyone can read the
file, nobody can execute it, and you are the only user that can write to it.

> The `-` at the very beginning of the line in the terminal means that the permissions
> are referring to a file. If you were getting permissions to a directory, you would see
> a `d` in the front for "directory".

## Directory permissions

The permissions for directories are similar but distinct for files. Though directories
use the same `rwx` format, the symbols have slightly different meanings.

- `r` list directory contents using `ls` command;
- `w` add or remove files or directories;
- `x` enter directory using `cd` command;

Setting appropriate permissions on directories is a best practice for both security and
stability reasons.

> You may see an `s` permission. The `s` stands for "special permission". It means that
> any new files created within the directory will have their group ownership set to be
> the same as the directory owner.

## Executable files

A Linux file is executable if it contains instructions that can be directly interpreted
by the operating system. Basically, an executable file is a ready-to-run program. They
are also referred to as binaries or executables.

Formally speaking, for a text file to be considered an executable shell script for a
given user, it needs to have two things:

1. execute permissions set for that user;
2. a directive, called "shebang", in it first line to declare itself to the operating
system as a binary;
