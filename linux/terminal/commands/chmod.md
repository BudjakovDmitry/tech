# chmod

Change or modify file or directory permissions (chmod stands for "change mod").

[Managing file permissions and ownership](/linux/file_permissions.md)

Specify which permissions to change with a combination of the following characters:

- **permissions**: `r` - read, `w` - write, `x` - execute;
- **user categories**: `u` - user, `g` - group, `o` - all others;
- **operations**: `+` - grand, `-` - revoke;

For example: revoke read permissions from your group and all other users

```shell
chmod go-r my_file
```

In this case we remove read (r) permissions for group (g) and others (o).

More examples:

```shell
# make file executable for all users
chmod +x script.sh

# revoke read permissions for all users
chmod -r users.txt

# revoke read permissions only for 'other' category
chmode o-r users.txt
```
