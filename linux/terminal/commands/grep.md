# grep

Return lines of a file matching a specified pattern, such as a regular expression. Grep
stands for "Global Regular Expression Print".

Suppose we have a list of people's names.

```
Alan Turing
Bjarne Stroustroup
Charles Babbage
Dennis Ritchie
Erwin Schrodinger
```

Find all lines that contains the consecutive characters "ch":

```shell
grep ch people.txt
```

will return

```
Dennis Ritchie
Erwin Schrodinger
```

## Options

### -c

Get the count of matching lines;

### -i

Make search case-insensitive (by default it is case-sensitive).

```shell
grep -i ch people.txt
```

will return

```
Charles Babbage
Dennis Ritchie
Erwin Schrodinger
```

### -n

Also print the line numbers;

### -r

Use `-r` option to perform a recursive search which will include all files under a
directory, subdirectories and their files.

If we don't specify a starting directory, grep will search the current working
directory.

```shell
# search the current working directory and any nested directories
grep -r "chicken"
```

### -v

Print all lines which do not contain the pattern;

### -w

Match only if the pattern matches whole words rather than fragments located inside of
the words.
