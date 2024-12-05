# tee

The tee program reads standard input and copies it both to standard output and to a
file. This allows us to capture information part of the way through a pipeline, without
interrupting the flow.

```shell
command1 | tee file.txt | command2 ...
```

```shell
ls /usr/bin | tee ls.txt | grep gzip
```

If we put `tee` in the middle of two pipes (example above), it is going to take output
coming from one command, save it to a file that we specify and pass it to the next
command.
