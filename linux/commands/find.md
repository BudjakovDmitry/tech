# find

Find files matching a pattern in the current directory tree. You can search for files
based on different attributes, such as the file's name, type, owner, size, or timestamp.

The find command conducts a search of the entire directory tree starting from the given
directory name.

## Arguments

Path to the directory where search. You can search for files based on different
attributes, such as the file's name, type, owner, size or timestamp.

```shell
# search within a current directory
find . -name 'a.txt'

# find all .txt files in the /etc directory
find /etc -name '*.txt'
```

## Options

### -name

Name of a file which need to find (case-sensitive).

```shell
find . -name 'a.txt'
```

### -iname

Name of file which need to find (case-insensitive).

```shell
find . -iname 'a.txt'
```
