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


### -and

`find expr1 -and expr2` is the same as `find expr1 expr2`

### -amin n

File was last accessed less than, more than or exactly *n* minutes ago.

```shell
# find files that were accessed exactly ten minutes ago
find -amin 10

# find files that were accessed more than ten minutes ago
find -amin +10

# find files that were accessed less than ten minutes ago
find -amin -10
```

### -atime n

File was last accessed less than, more than or exactly *n\*24* hours ago. When *find*
figures out how many 24-hours periods ago file was last accessed, any fractional parts
is ignored. So to match `-atime +1`, a file has to have been accessed at least **two**
days ago.

```shell
# find files that were last accessed exactly 24 hours ago
find -atime 1

# find files that were last accessed more than 48 hours ago
find -atime +2

# find files that were last accessed less than 48 hours ago
find -atime -2
```

### -cmin n

File's status was last changed less than, more than or exactly *n* minutes ago.

```shell
# find files that were changed exactly one minute ago
find -cmin 1

# find files that were changed more than ten minutes ago
find -cmin +10

# find files that were changed less then ten five minutes ago
find -cmin -5
```

### -ctime n

File's status was last changed less than, more than or exactly *n\*24* hours ago. See
the comments for `-atime` to understand how rounding affects the interpretation of file
status change times.

```shell
# find files that were changed exactly 24 hours ago
find -ctime 1

# find files that were changed more than 48 hours ago
find -ctime +2

# find files that were changed less than 48 hours ago
find -ctime -2
```

### -empty

Find empty files and/or directories.

```shell
# find all empty files and directories in user's home directory
find ~ -empty
```

```shell
# find all empty files in user's home directory
find ~ -empty -type f
```

```shell
# find all empty directories in user's home directory
find ~ -empty -type d
```

### -exec *command*

```shell
find -exec command {};
```

Execute command. All following arguments to **find** are taken to be arguments to the
*command* until an argument consisting of `;` is encountered. The string `{}` is
replaced by the current file name being processed everywhere it occurs in the arguments
to the command.

```shell
find -type f -empty -exec ls -l '{}' ';'
```

> Note: the `ls` command will execute for every pathname. For example, if `find` command
> returns 10 files, the `ls` command wil runs 10 times for each file.

```shell
find ~ -type f -name "*.txt" -exec grep "hello" '{}' ';'
```

The next example finds all files that end with `.html`. It then creates a copy of each
one using the `cp` command. Each of the copies ends with "_COPY" so we end up with
files like "index.html_COPY" and "navbar.html_COPY".

```shell
find -type f -name "*.html" -exec cp '{}' '{}_COPY' ';'
```

### -ok *command*;

Like `-exec` but ask the user first. If the user agrees, run the command. Otherwise just
return false.

```shell
find -empty -ok rm '{}' ';'
```

### -l, --files-with-matches

Suppress normal output; instead print a name of each input file from which output would
normally have been printed. Scanning each input file stops upon first match.

### -mmin n

File's data was last modified less than, more than or exactly *n* minutes ago.

```shell
# find files that were modified exactly 30 minutes ago
find -mmin 30

# find files that were modified more than 30 minutes ago
find -mmin +30

# find files that were modified less than 30 minutes ago
find -mmin -30
```

### -mtime n

File's data was last modified less than, more than or exactly *n\*24* hours ago. See the
comments for `-atime` to understand how rounding affects the interpretation of file
modification times.

```shell
# find files that were modified exactly 24 hours ago
find -mtime 1

# find files that were modified more than 48 hours ago
find -mtime +2

# find files that were modified less than 48 hours ago
find -mtime -2
```

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

### -not

Negates whatever options comes after it.

```shell
# find files that NOT ends with '.html'
find -type -f -not -name '*.html'

# find all files in user's home directory that were changed less than one minute ago and
# don't end with '.xml'
find ~ -mmin -1 -not -name '*.xml'
```

The shortcut for `-not` is `!`

```shell
# these commands have the same result
find -not -name '*.txt'
find ! -name '*.txt'
```

### -iname

The same as `-name` but case-insensitive.

```shell
find /home -iname "documents"
```

### -or

```shell
# print all html and css files
find . -name '*.html' -or -name '*.css'
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
