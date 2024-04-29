# mkdir

Make a new directory.

```shell
mkdir /path/to/dir
```

Create five directories:

```shell
mkdir dir1 dir2 dir3 dir4 dir5
# or
mkdir dir{1,2,3,4,5}
```

## Options

### -p, --parents

Use this option if you want to create more than one directory that is nested.

```shell
mkdir pets/cats/kitties
```

It will make *pets* directory and *cats* directory inside *pets* and *kitties* directory
inside *cats*.
