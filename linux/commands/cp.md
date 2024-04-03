# cp

Copies files or directories.

| Example | Result                                                                                                                                                                                                                                                                                      |
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `cp file1 file2` | Copy *file1* to *file2*. If *file2* exists, it is overwritten with the contants of *file1*. If *file2* does not exists, it is created.                                                                                                                                                      |
| `cp -i file1 file2` | Same as previous command, except that if *file2* exists, the user is prompted before it is overwritten.                                                                                                                                                                                     |
| `cp file1 file2 dir` | Copy *file1* and *file2* into directory *dir1*. The directory *dir1* must already exist.                                                                                                                                                                                                    |
| `cp dir1/* dir2` | Copy all the files in *dir1* into *dir2*. The directory *dir2* must already exist.                                                                                                                                                                                                          |
| `cp -r dir1 dir2` | Copy the contents of directory *dir1* to directory *dir2*. If directory *dir2* does not exists, it is created and, after the copy, will contain the same contents as directory *dir1*. If directory *dir2* does exist, then directory *dir1* (and its contents) will be copied into *dir2*. |

```shell
cp /path/to/file.txt other/path/to/
```

### options

| Option | Description                                                                                                                                                                                                        |
|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-a` | copy the files and directories and all of their attributes, including ownership and permissions. Normally, copies take on the default attributes of the user performing the copy.                                  |
| `-i` | before overwriting an existing file, prompt the user for information. If this option is not specified, `cp` will silently overwrite files.                                                                         |
| `-r` | Copy directories recursively. Copy *dir1* with all its content inside *dir2*: `cp -r /source/dir/ /dest/dir2/`. Copy contents of a directory to a new directory (which is not created yet): `cp -r dir1/ new_dir/` |
| `-u` | when copying files from one directory to another, only copy files that either don't exist or are newer than the existing corresponding files in the destination directory. This is useful when copying large number of files as it skips files that don't need to be copied. |
| `-v` | display informative messages as the copy is performed. |

###
