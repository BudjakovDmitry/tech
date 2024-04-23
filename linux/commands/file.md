# file

Determine a file's type.

Filenames in Linux are not required to reflect a file's contents. The `file` command
don't look at file's extension.

```shell
file book.pdf
book.pdf: PDF document, version 1.5
```

Command above will print brief description of the file's contents.

We can pass multiple file names:

```shell
file book1.pdf citty_image.png, logfile
```

In fact, one of the common ideas in Unix-like operating systems such as Linux is that
"everything is a file".
