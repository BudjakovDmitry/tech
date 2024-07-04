# Regular expressions

`.` matches any single character.

```shell
grep "p...." file.txt
```

`^` matches the start of a line.

```shell
# matches all lines start from "if"
grep "^if" file.txt
```

`$` matches the end of a line.

```shell
# matches all lines end with "me"
grep "me$" file.txt
```

`[abc]` matches any character in the set

Ranges examples:

- `[0-9]` numbers;
- `[5-9]` numbers from 5 to 9;
- `[A-Z]` capital letters;
- `[a-z]` lowercase letters;

```shell
# match both parmasan and parmesan
grep "parm[ae]san" recipies.txt

# match 21, 22, 23
grep "2[1-3]" numbers.txt
# the same result
grep "2[123]" numbers.txt
```

`[^abc]` matches any char NOT in set.

```shell
# match 26, 27, 28, 29
grep "2[^1-5]" numbers.txt
```

`?` match 0 or 1 of the preceding expression

```shell
# match lines with 'bird' and 'birds'
egrep "birds?" file.txt
```

`a{n}` means n "a" characters in a row.

```shell
# 5 capital letters in a row
egrep "[A-Z]{5}" file.txt

# 3 vowels in a row
egrep "[aeiou]{3}" file.txt

# match from 2 to 4 vowels it a row (2 or 3 or 4 vowels in a row)
egrep "[aeiou]{2,4}" file.txt
```
