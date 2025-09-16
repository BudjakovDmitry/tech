# Filesystem

## Using wildcards

You can use [wildcards](wildcards.md) in filenames. Using wildcards (which is also known
as *globbing*) allows you to select filenames based on patterns of characters.

## inodes

inode is a data object that contains metadata about the files within your file system.
inodes contains the information like the size of the file, who owns it, the permission
string and more, other than the name of the file and the content of the file.

Every file or directory has an inode.

Every storage medium have its own set of inodes. For example:

```shell
ls -li ~john
6921 -rw-rw-r-- 1 john john 85 Apr 3 12:08 README.MD
```

File README.MD has an inode number 6921. This file is located in John's home directory
in local file system, it is not on flash drive or external storage device. This inode
number would have absolutely no meaning when it comes to a flash drive. Because every
storage medium has its own set of inodes. If we were to move this file to a flash drive
it would get a different inode.
