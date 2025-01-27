# tar

`tar` command allows us to combine multiple files into one archive file. The .tar file
isn't compressed.

```shell
# create archive
tar -cf my_archive.tar /path/to/file/or/dir
```

```shell
# look inside a tar file without extracting content
tar -tf my_archive.tar
```

```shell
# extract files from tar archive
tar -xf my_archive.tar
```

## Options

### -c

Create archive.

### -f

Provide a filename.

### -t

List files inside a tar file.

### -v

Verbose mode. Add more information to output.

### -x

Extract.

## Arguments

Path to file or a directory
