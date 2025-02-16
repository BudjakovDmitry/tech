# wc

Wc stands for word count. Get count of lines (new line characters), words and byte
counts in file.

For example, we have file *notes.txt* with following content:

```
foo
foo
bar
```

Command

```shell
wc notes.txt
```

Will return

```
3  3  12  notes.txt
```

This output means, that file *notes.txt* contains 3 lines, 3 words and 12 characters.
Note that `wc` also counts new line characters. In our example we have three regular
characters and one new line character in each line (total: 3*4=12 characters).


## Options

### -c, --bytes

Print the byte count

```shell
wc -c notes.txt
```

will return

```
12  notes.txt
```

### -l

View only line count.

```shell
wc -l notes.txt
```

will return

```
3  notes.txt
```

### -m, --chars

Print the character counts


### -w

View only word count.

```shell
wc -w notes.txt
```

will return

```
3  notes.txt
```
