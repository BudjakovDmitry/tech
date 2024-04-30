# sort

Sort the lines of a fine alpha-numerically and print the sorted result to standard
output. It doesn't change the file itself.

```shell
sort pets.txt
```

Will return something like

```
dog
dog
dog
humster
humster
parrot
```

Sorting algorithm of this command does not put all uppercase letters before lowercase
letters. For example:

```
a
f
A
r
F
z
R
```

Will be sorted in the next order:

```
a
A
f
F
r
R
z
```

## Options

### -k

We can specify a particular "column" that we want to sort by, using "-k" option,
followed by a field number. For example, file *price_list* (columns: name, price, units
in stock):

```
racecar 49.00 3
chocolate 19.99 12
pencil 0.50 49
house 199.99 1
pizza 5.00 1
fish 13 2
```

By default `sort` command will sort by alphabetically comparing each line from the
beginning. To specify column use `-k` option.

```shell
sort -nk 2 price_list
# or
sort -n -k2 price_list
```

### -n, --numeric-sort

By default, numbers compares as strings, not like numbers. To compare them as numbers
use `-n` option. For example, we have a file
*prices*:

```
49.00
19.99
0.50
199.99
5.00
13
```

```shell
sort prices
```

```
0.50
13
19.99
199.99
49.99
5.00
```

```shell
sort -n prices
```

```
0.50
5.00
13
19.99
49.00
199.99
```

### -r, --reverse

Get lines sorted in reverse order.

```shell
sort -r pets.txt
```

```
parrot
humster
humster
dog
dog
dog
```

### -u, --unique

Prints only unique strings in the output.

```shell
sort -u pets.txt
```

```
dog
humster
parrot
```
