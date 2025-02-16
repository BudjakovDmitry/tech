# tac

tac (cat spells backwards) does mostly the same things as `cat`. It concatenates and
prints files in reverse order. You cat think of it as printing in reverse "vertically".
Original file does not changes.

```shell
cat numbers.txt
```

```
one
two
three
four
```

```shell
tac numbers.txt
```

```
four
three
two
one
```

We can use `tac` with more than one file.

```shell
tac numbers.txt numbers.txt
```

```
four
three
two
one
four
three
two
one
```
