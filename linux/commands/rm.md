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

### -r

Remove directories and their contents recursively.

```shell
rm -r /path/to/dir
```

If you want to remove an empty directory, `rm -rf` is not recommended. Instead, you
should use `rmdir` command. This guarantees that you'll never accidentally delete any
important files or directories.

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

### -f

Ignore nonexistent files and do not prompt. This overrides the `-i` option.

If `file.log` does not exists, rm will continue silently.

```shell
rm -f file.log
```

### -v

Display informative messages as the deletion is performed.
