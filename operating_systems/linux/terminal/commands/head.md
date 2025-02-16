# head

Print first N lines of a file. By default, it prints first 10 lines.

```shell
# print first 10 lines
head users-info.txt
```

## Options

### -c, --bytes

Print the first NUM bytes of each file.

```shell
head -c 10 names.txt
```

### -n, --lines

Specify a number of lines to print.

```shell
# print first 5 lines
head -n 5 users-info.txt
head -5 users-info.txt
```
