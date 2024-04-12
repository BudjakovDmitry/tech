# paste

Merge line from the multiple files.

Imagine we have three text files, all with the same number of lines:

```
# first.txt
Alan
Bjarne
Charles
```

```
# last.txt
Turing
Stroustrup
Babbage
```

```
yob.txt
1912
1950
1791
```

```shell
paste first.txt last.txt yob.txt
```

will return

```
Alan    Turing     1912
Bjarne  Stroustrup 1950
Charles Babbage    1791
```

`paste` uses a tab as a default delimiter (use `-d` option to specify delimiter).

## Option

### -d

Specify delimiter.

```shell
paste -d "," first.txt last.txt yob.txt
```
