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

If `cat` is not given any arguments, it reads from standard input, and since stdin, by
default, attached to the keyboard, it's waiting for us to type something. In this case
`cat` copies standard input to standard output, so we see our line of text repeated.

```shell
cat
# waiting to type something and repeat this
```

We can also redirect to standard input manually.

```shell
cat < names.txt
```

These two commands `cat names.txt` and `cat < names.txt` have the same result, but the
way that we got there is different. In the first example we pass file as an argument,
in the second example we pass the file to standard input.

We can use this behaviour to create short text files.

```shell
cat > lazy_dog.txt
# entered text will saved in lazy_dog.txt
```
