# tail

Print last N lines of a file. By default, it prints last 10 lines.

```shell
# print last 10 lines
tail users-info.txt
```

## Options

### -c, --bytes

Output the last NUM bytes.

```shell
tail -c 10 names.txt
```

### -f, --follow

Output appended data as file grows.

```shell
tail -f /var/log/syslog
```

Press `Ctrl + c` to get back to terminal prompt.

### -n, --lines

Specify a number of lines to print.

```shell
# print last 5 lines
tail -n 5 users-info.txt
tail -5 users-info.txt
```
