# tr

Translate, squeeze and/or delete characters from standard input, writing to standard
output.

```
tr [OPTION]... SET1 [SET2]
```

## Options

### -d, --delete

Delete characters in `SET1`, do not translate

```shell
echo "she is smart" | tr -d s
# he i mart
```

## Examples

```shell
# replace lowercase s to uppercase S
echo "she is smart" | tr s S
# She iS Smart
```

```shell
# replace all lowercase to uppercase
echo "she is smart" | tr a-z A-Z
# SHE IS SMART
```

We can use [character classes](/linux/wildcards.md)

```shell
echo "The pin code is: 5476" | tr [:digit:] "*"
# The pin code is: ****
```
