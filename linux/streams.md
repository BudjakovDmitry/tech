# Standard streams

The three standard data streams are communication channels between a computer program
and its environment.

They are:

- Standard Input;
- Standard Output;
- Standard Error;

Each stream gets its own numeric file descriptor:

- Standard input - 0;
- Standard output - 1;
- Standard error - 2;

## Standard Input

Standard input is where a program or command gets its input information from. By
default, the shell directs standard input from the keyboard.

The input information could come from a keyboard, a file, or even from another command.

## Standard Output

Standard output is a place to which a program or command can send information.

The information could go to a screen to be displayed (default behaviour), to a file, or
even to a printer or other devices.

## Standard Error

Commands and programs also have a destination to send error messages: standard error.

By default, the shell directs standard error information to the screen for us to read,
but we can change that destination if needed.

## Redirection

### Redirecting output

The redirect output symbol `>` tells the shell to redirect the output of a command to a
specific file instead of a screen.

```
command > filename
```

```shell
date > today.txt
```

The file does not exist, it will be created. If file exists, its contents will be
overwritten.

To add new content to the end of the file, use `>>` when redirecting.

```shell
echo "hello" >> greetings.txt
echo "world" >> greetings.txt
```

The `>` (and `>>`) operator actually defaults to using 1 as the file descriptor number,
which is why wi didn't need to specify `1>` (or `1>>`) to redirect standard output
(through we can).

### Redirecting input

To pass the contents of a file to standard input, use the `<` symbol followed by the
filename.

```
command < filename
```

```shell
cat < names.txt
```

The `<` operator uses as default file descriptor number of 0, so we don't need to
specify `0<` to redirect to standard input (through we can)

### Redirecting errors

By default, error messages are output to the screen, but we can change this by
redirecting standard error. The standard error redirection operator is `2>`.

```shell
command 2> filename
```

To append new content to the end of the file use `2>>`

```shell
command 2>> filename
```

### Redirecting all streams together

```shell
# redirect standard input from original.txt
# redirect standard output to output.txt
sort < original.txt > output.txt
```

```shell
# redirect standard output to a file animals.txt
# redirect standard error to a file error.txt
cat cats.txt dogs.txt > animals.txt 2> error.txt
```

If you are going to redirect to both standard output and standard error, you need to do
standard output first.

If we want to redirect both standard output and standard error to the same file, we
could type this:

```shell
ls docs > output.txt 2> output.txt
```

Or we can instead use `2>&1` which is a fancy syntax for saying "redirect standard error
to the same location as standard output (or whatever has file descriptor #1)".

```shell
ls docs > output.txt 2>&1
```

Newer versions of bash also support a fancier syntax or redirecting both standard output
and standard error to the same file: `&>` notation:

```shell
ls docs &> output.txt
# or
ls doct &>> output.txt
```
