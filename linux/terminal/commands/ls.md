# ls

List the contents of the directory.

```shell
# list contents of current working directory
ls
```

## Options

### -a, --all

List all files, even those with names that begin with a period (`.`), which are normally
not listed (that is, hidden).

### -A, --almost-all

Like the `-a` option except it does not list `.` (current directory) and `..` (parent
directory).

### -c

By default, when you type `ls -l` we see *modification time*. If you want to see
*change time* type `ls -lc`. [More about timestamps](/linux/timestamps.md).

### --color[=WHEN]

colorize the output; WHEN can be 'always' (default if omitted), 'auto', or 'never'.

### -d, --directory

Ordinarily, if a directory is specified, it will list the contents of the directory, not
the directory itself. Use this option in conjunction with the `-l` option to see details
about the directory rather than its contents.

```shell
ls -l dir/  # shows info about directory's content
ls -ld dir/  # shows info about directory itself
```

### -F, --classify

Option will append an indicator character to the end of each listed name. For example,
it will append a forward slash (`/`) if the name is a directory.

### -h, --human-readable

In long format listings (`-l` and `-s`) print file sizes in human-readable format rather
than in bytes (like 1K, 234M, 2G, etc.).

```bash
ls -lh
```

### -i

Print the index number of each file (inode).

### -l

Show child files and directories in a more detailed format which shows permissions,
last-modified date, owner, etc. (long format).

### -m

Print result as comma separated list of entities.

### -r, --reverse

Reverse the sort order. Normally, `ls` displays its results in ascending alphabetical
order.

```
ls -r

ls -ltr
```

### -R, --recursive

List subdirectories recursively.

### -S

Sort results by file size, largest first.

### --sort=WORD

Sort by WORD instead of name: none (`-U`), size (`-S`), time (`-t`), version (`-v`),
extension (`-X`).

### -t

Sort by modification time, newest first.

```shell
ls -lt
```

### -u

By default, when you type `ls -l` we see *modification time*. If you want to see
*access time* type `ls -lu`. [More about timestamps](/linux/timestamps.md).


### -R

List subdirectories recursively.

### -1

List one file per line.

## Long look format

Example of the output in long format:

```shell
-rw-r--r-- 1 root root 3576296 2017-04-03 11:05 Experience ubuntu.ogg
-rw-r--r-- 1 root root 1186219 2017-04-04 11:05 kubuntu-leaflet.png
-rw-r--r-- 1 root root   47584 2017-04-03 11:05 logo-Edubuntu.png
drwxrwxr-x 2 root root    4096 2027-04-01 17:34 materials
```

| Field              | Meaning                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-rw-r--r--`       | Access rights to the file. The first character indicates the type of file. Among the different types, a leading dash (`-`) means a regular file, `d` indicates a directory and `l` indicates a symbolic link, `c` - character device, `b` - block device (for example disks). The next three characters are the access rights for the file’s owner, the next three are for members of the file’s group, and the final three are for everyone else; |
| `1`                | File’s number of hard links.                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `root`             | The username of the file’s owner.                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `root`             | The name of the group that owns the file.                                                                                                                                                                                                                                                                                                                                                                                                          |
| `32059`            | Size of the file in bytes.                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `2017-04-03 11:05` | Date and time of the file’s last modification.                                                                                                                                                                                                                                                                                                                                                                                                     |
| `oo-cd-cover.odf` | Name of the file.                                                                                                                                                                                                                                                                                                                                                                                                                                  |

## Arguments

The path to a directory you would like to explore. If it is not given `ls` will list the
contents of the current working directory. Otherwise, it will return the contents of
given directory.

```shell
ls /bin
```

We can even specify multiple directories.

```shell
ls /bin /opt
```

Show information about file:

```shell
ls -l script.sh
```

```shell
# list all files starting with 'b' in the /bin directory
ls /bin/b*

# list all files ending in 'r' in the /bin directory
ls /bin/*r
```
