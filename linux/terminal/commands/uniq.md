# uniq

Filter out the repeated lines. It accepts a list of data from either standard input or a
single file.

Note, that the `uniq` command only removes duplicated lines if they are consecutive.

For example, file *pets.txt*:

```
dog
dog
dog
parrot
parrot
dog
```

```shell
uniq pets.txt
```

will return

```
dog
parrot
dog
```

Usage example:

```shell
ls /bin /usr/bin | sort | uniq | less
```

## Options

### -d, --repeated

Only print duplicate lines, one for each group

```shell
ls /bin/ /usr/bin/ | sort | uniq -d | less
```
