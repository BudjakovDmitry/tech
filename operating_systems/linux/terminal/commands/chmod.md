# chmod

## Symbolic notation

Specify which permissions to change with a combination of the following characters:

- **permissions**:
  - `r` - the read permission;
  - `w` - the write permission;
  - `x` - the execute permission;
- **user categories**:
  - `u` - user (the owner of the file);
  - `g` - group (members of the group the file belongs to);
  - `o` - all others (the "world");
  - `a` - all of the above;
- **operations**:
  - `+` - grand the permission;
  - `-` - revoke the permission;
  - `=` - set a permission and removes others;

### Examples

__Example 1__: add write permissions to the group
```shell
# before -rw- r-- r--
chmod g+w file.txt
# after -rw- rw- r--
```

__Example 2__: Remove write permissions from all

```shell
# before -rw- rw- r--
chmod a-w file.txt
# after -r-- r-- r--
```

__Example 3__: Add executable permissions for owner

```shell
# before -rw- rw-r--
chmod u+x file.txt
# after -rwx rw- r--
```

__Example 4__: set permissions for read ONLY for all

```shell
# before -rwx rwx r--
chmod a=r file.txt
# after -r-- r-- r--
```

__Example 5__: revoke read permissions from your group and all other users

```shell
# before -rw- rw- r--
chmod go-r file.txt
# after -rw- -w- ---
```

__Example 6__: make file executable for all users

```shell
# before -rw- -w- ---
chmod +x script.sh
# after -rwx -wx --x
```

__Example 7__: revoke read permissions for all users

```shell
# before -rwx rwx- --x
chmod -r file.txt
# after --wx -wx --x
```

__Example 8__: revoke read permissions only for 'other' category

```shell
# before -rw- rw- r--
chmode o-r file.txt
# after -rw- rw- ---
```

__Example 9__: add write and execute permissions for owner

```shell
# before -r-- r-- r--
chmod u+wx file.txt
# after -rwx r-- r--
```

__Example 10__: combination

chmod u+rwx,g-x+rw,o-rwx file

## Octal notation

chmod also supports another way of representing permission patterns: octal numbers (base
8). Each digit in an octal number represents 3 binary digits.

| Octal | Binary | File mode |
|-------|--------|-----------|
| 0     | 000    | ---       |
| 1     | 001    | --x       |
| 2     | 010    | -w-       |
| 3     | 011    | -wx       |
| 4     | 100    | r--       |
| 5     | 101    | r-x       |
| 6     | 110    | rw-       |
| 7     | 111    | rwx       |

For every spot in a permission statement, there are two choices: a letter (for example
`w`) or a dash (`-`). It can be represented in binary numbers 0 - is a dash and 1 is a
number. These binary numbers are equivalent to just a shorter octal numbers.

### Examples

```shell
chmod 755 file.txt
# -rwx r-x r-x
```
