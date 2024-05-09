# Piping

Piping is passing the output of one command to the standard input of the other command.
We use pipe character (`|`) to separate two commands.

```
command1 | command2
```

```shell
date | rev
# 4202 TDI MA 31:52:60 8  yaM deW
```

```shell
ls -l /usr/bin/ | less
```

```shell
ls -1 /usr/bin/ | wc -l
```
