# cat

The `cat` command con**cat**enates and prints the contents of files.

In simplest way this command will read the contents of the file and print them out.

```shell
cat instructions.txt
```

If we provide cat with multiple files, it will concatenate their contents and output
them.

```shell
cat one.txt two.txt
```

## Options

### -n, --number

Number all output lines.

## Arguments

The path to a file.

```shell
cat names.txt
```

The `cat` command is set up to accept filenames as arguments directly, but we can also
redirect to standard input manually.

```shell
cat < names.txt
```

These two commands `cat names.txt` and `cat < names.txt` have the same result, but the
way that we got there is different. In the first example we pass file as an argument,
in the second example we pass the file to standard input.
