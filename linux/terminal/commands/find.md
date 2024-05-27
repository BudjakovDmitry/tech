# find

Find files matching a pattern in the current directory tree. You can search for files
based on different attributes, such as the file's name, type, owner, size, or timestamp.

The find command conducts a search of the entire directory tree starting from the given
directory name.

Example: print out the list of every single file and directory nested in the current
working directory including files and folders nested in subdirectories.

```shell
find
```

## Arguments

Path to the directory where search.

```shell
# find all files and directories in user's home directory
find ~
```

## Options

### -name

We can provide a specific pattern to `find` to use when matching filenames and
directories with the `-name` option. We need to enclose our pattern in quotes.

The `-name` option is case-sensitive.

```shell
# find all files in Documents folder that end in the '.txt'
find ~/Documents -name "*.txt"
```

It is important ot understand if we write `find ~ -name "right"` the command is not
going to do a search for partial match of "right". It's going to look a file or
directory called exactly "right". If we want to find all files or directories that end
with "right", we should use other pattern `find ~ -name "*right"`.

```shell
# find any file or directory inside home directory that contains a number
find ~ -name "*[[:digit:]]*"
```

### -iname

The same as `-name` but case-insensitive.

```shell
find /home -iname "documents"
```

### -size

The `-size` option is used to find files of a specific size.

```shell
# find all files larger than 1 gigabyte
find -size +1G
```

```shell
# find files under 50 megabytes
find -size -50M
```

```shell
# find files that are exactly 20 kilobytes
find -size 20k
```

### -type

We can tell `find` to only find by file type: only print files, directories, symbolic
links, etc.

```shell
# print a list of every file inside current working directory
find -type f
```

```shell
# print a list of every directory inside of current working directory
find -type d
```

```shell
# print a list of symbolic links inside current working directory
find -type l
```

### -user

The `-user` option uses to match files and directories that belong to a particular user.

```shell
# find all fies that in /home directory that belong to harry
find /home -user harry
```
