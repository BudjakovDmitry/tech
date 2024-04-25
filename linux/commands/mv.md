# mv

Move a file or directory. You can use this command to move files from one directory to
another and/or rename them. In either case, the original filename no longer exists after
the operation.

You should also always be caution when moving a file. If the target file already exists,
it will be overridden, or replaced, by the source file.

When the source and the target directories/files are the same, you can use `mv` to
rename a file/directory.

## Options

### -i

Before overwriting an existing file, prompt the user for confirmation. If this option is
not specified, `mv` will silently overwrite files.

### -u

When moving files from one directory to another, only move files that either don't exist
or are newer than the existing corresponding files in the destination directory.

### -v

Display informative messages as the move is performed

## Examples

Move *file1* to *file2*. If *file2* exists, it is overwritten with the contents of
*file1*. If *file2* does not exist, it is created. In either case, *file1* cases to
exist.

```shell
mv file1 file2
```

---

Same as the previous command, except that if *file2* exists, the user is prompted before
it is overwritten.

```shell
mv -i file1 file2
```

---

Move *file1* and *file2* into directory *dir1*. The directory *dir1* must already exist.

```shell
mv file1 file2 dir1/
```

---

If directory *dir2* does not exist, create directory *dir2* and move the contents of
directory *dir1* into *dir2* and delete directory *dir1*. If directory *dir2* does
exist, move directory *dir1* (and its contents) into directory *dir2*.

```shell
mv dir1/ dir2/
```
