# sort

Sort the lines of a fine alpha-numerically and print the sorted result to standard
output.

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

## Options

### -r

Long format: `--reverse`

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

### -u

Long format: `--unique`

Prints only unique strings in the output.

```shell
sort -u pets.txt
```

```
dog
humster
parrot
```
