# ln

The `ln` command is used to create either hard or symbolic [links](/linux/links.md).

Symbolic link:

```shell
ln -s item link
```

where *item* is either a file or a directory.

```shell
ln -s /home/john/report.txt /home/john/Desktop/
```

`/home/john/report.txt` - path to the file, what we link to.

`/home/john/Desktop/` - path where we want the link will show up.

You should be very careful with relative paths in symbolic links, because link will try
to find target using relative path starting from link location. If you change link
location it can break.

For example, we have file system like this:

```
/home/me/
 - file
 - /dir
```

We are located inside `/home/me` and want to create symlink in `dir` referenced to the
`file`:

```shell
ln -s ../file dir/file-symlink
```

Remember that when we create a symbolic link, we are creating a text description of
where the target file is relative to the symbolic link.

Symlink to the directory:

```shell
ln -s dir1 dir1-sym
```

Hard link:

```shell
ln file link
```

```shell
ln /var/logs/app_log /home/john/logs
```
