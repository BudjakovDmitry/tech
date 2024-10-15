# Parameter expansion

If we write out the name of an environment variable prefixed with a dollar sign (`$`),
the shell will replace it with the actual value.

```shell
echo $USER
```

There is no error if we're trying reference a variable that does not exist. We just get
nothing.

```shell
# no error
echo $NOT_EXISTING_VARIABLE
```
