# Standard streams

The three standard data streams are communication channels between a computer program
and its environment.

They are:

- Standard Input;
- Standard Output;
- Standard Error;

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

### Redirecting input

To pass the contents of a file to standard input, use the `<` symbol followed by the
filename.

```
command < filename
```

```shell
cat < names.txt
```
