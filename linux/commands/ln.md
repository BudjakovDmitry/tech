# ln

The `ln` command is used to create either hard or symbolic links.

Symbolic link:

```shell
ln -s /home/john/report.txt /home/john/Desktop/
```

`/home/john/report.txt` - path to the file, what we link to.
`/home/john/Desctop/` - path where we want the link will show up.

You should be very careful with relative paths in symbolic links, because link will try
to find target using relative path starting from link location. If you change link
location it can break. It is good idea always to use absolute paths while creating
symbolic links.

Hard link:

```shell
ln /var/logs/app_log /home/john/logs
```
