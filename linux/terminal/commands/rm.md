# rm

Remove file or directory. By default, it does not remove directories.

Delete file silently:

```shell
rm access.log
```

Delete multiple files:

```shell
rm app.js style.css imdex.html
```

We can pass a relative or absolute path to the file.

## Options

### -d, --dir

Remove a directory if it is empty.

### -f, --force

Ignore nonexistent files and do not prompt. This overrides the `-i` option.

If `file.log` does not exists, rm will continue silently.

```shell
rm -f file.log
```

### -i

Prompt before every removal (`y` to confirm deletion, `n` to deny deletion). If this
option is not specified, `rm` will silently delete files.

```shell
rm -i *.log
```

> When you are only removing one file with `rm` command, the `-i` option is redundant.
> But if you want to remove multiple files, for example by using a wildcard to find all
> filenames matching a pattern, it's best practice to confirm or deny each deletion by
> including the `-i` option.


### -r, --recursive

Remove directories and their contents recursively. This means that if a directory being
deleted has subdirectories, delete them too. To delete a directory, this option must be
specified.

```shell
rm -r /path/to/dir
```

If you want to remove an empty directory, `rm -rf` is not recommended. Instead, you
should use `rmdir` command. This guarantees that you'll never accidentally delete any
important files or directories.

### -v, --verbose

Display informative messages as the deletion is performed.

## Examples

Delete *file* and *dir* and its content

```shell
rm -r file dir
```

Same as the previous command except that if either *file* or *dir* does not exist, `rm`
will continue silently.

```shell
rm -rf file dir
```
