# uniq

Filter out the repeated lines.

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
