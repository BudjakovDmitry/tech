# xargs

Build and execute command lines from standard input.

Some commands don't accept standard input. The next example will not work because the
'ls' command doesn't accept standard input. 

```shell
# this is doesn't work
find -empty | ls -l
```

The `xargs` command takes data from standard input that's passed to it, and then it
turns that into a bundle that can be provided as an argument list to some other command.
For example, `ls` can't work with standard input, but it accepts arguments.

```shell
find -empty | xargs ls -l
```

## Options

### -t, --verbose

Print the command line on the standard error output before executing it.

```shell
find -empty | xargs -t ls -l
# ls -l ./file1 ./file2
# -rw-rw-r-- ... ./file1
# -rw-rw-r-- ... ./file2
```
