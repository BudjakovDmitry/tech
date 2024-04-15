# wc

Get count of lines, words and characters in file.

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

### -l

View only line count.

```shell
wc -l notes.txt
```

will return

```
3  notes.txt
```

### -w

View only word count.

```shell
wc -w notes.txt
```

will return

```
3  notes.txt
```

### -c

View only character count.

```shell
wc -c notes.txt
```

will return

```
12  notes.txt
```
