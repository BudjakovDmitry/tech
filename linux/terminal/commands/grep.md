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

### -A NUM, --after-context=NUM

Print NUM lines of trailing context after matching lines.

### -B NUM, --before-context=NUM

Print NUM lines of leading context before matching lines.

### -C NUM, -NUM, --context=NUM

Print NUM lines of output context (NUM lines before and NUM lines after matching lines).

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

### -m NUM, --max-count=NUM

Stop reading a file after NUM matching lines.

### -n, --line-number

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

```shell
# specify directory
grep -r red ~/colors
```

### -v

Print all lines which do not contain the pattern;

### -w

Match only if the pattern matches whole words rather than fragments located inside of
the words.
