# usermod

`usermod` is a command that is used to change the properties of a user.

After creating a user we have to sometimes change their attributes like password or
login directory etc.

The information of a user is stored in the following files:

* `/etc/passwd`
* `/etc/group`
* `/etc/shadow`
* `/etc/login.defs`
* `/etc/gshadow`
* `/etc/login.defs`

When we execute usermod command the command make the changes in these files itself.

__Note__: `usermod` command needs to be executed only as a root user.

## Options

### -a, --append

Add the user to the supplementary group(s). Use only with the `-G` option.

### -G, --groups GROUP1[,GROUP2,...[,GROUPN]]

A list of supplementary groups which the user is also a member of. Each group is
separated from the next by comma with no intervening whitespace. The groups are subject
to the same restrictions as the group given with the `-g` option.

If the user is a currently a member of a group which is not listed, the user will be
removed from the group. This behaviour can be changed via the `-a` option, which appends
the user to the current supplementary group list.

## Arguments

Username

## Examples

```shell
# add user sam to the group students
sudo usermod -aG students sam
```
