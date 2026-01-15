# find

## Options

### -anewer reference

Time of the last access of the current file is more recent than that of the last data
modification of the *reference* file.

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

### -cnewer reference

Time of the last status change of the current file is more recent than that of the last
data modification of the *reference* file.

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

### -newer reference

Time of the last data modification of the current file is more recent than that of the
last data modification of the *reference* file.

```shell
find -newer notes.txt
```
