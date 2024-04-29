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

### -i

Make search case-insensitive.

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

### -c

Get the count of matching lines;

### -v

Print all lines which do not contain the pattern;

### -w

Match only if the pattern matches whole words;
