# cut

Extract a specific sections from each line of a file.

We have a file *people.txt*

```
Alan Turing
Bjarne Stroustroup
Charles Babbage
Dennis Ritchie
Erwin Schrodinger
```

Cut from specified index to specified index:

```shell
cut -c 2-9 people.txt
```

will return

```
lan Turi
jarne St
harles B
ennis Ri
rwin Sch
```

View only two first characters of each line:

```shell
cut -c -2 people.txt
```

View each line starting *from* the second character:

```shell
cut -c 2- people.txt
```

The `cut` command can also be used to extract a field from a delimited file (
`-d <delimiter>`).

Cut the last name of each person (each name consists of first name and last name,
separated by space):

```shell
$ cut -d ' ' -f2 people.txt
```

will return

```
Turing
Stroustroup
Babbage
Ritchie
Schrodinger
```

In our example delimiter is a space, and `-f2` tells to extract the second field.
