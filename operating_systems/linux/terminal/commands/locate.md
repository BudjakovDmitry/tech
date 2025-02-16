# locate

The `locate` command performs a search of pathnames across our machine that match a
given substring and then prints out any matching names.

It is speedy because it uses a pre-generated database file rather than searching the
entire machine.  For the same reason this command does not run relative to user's
current location.

For example:

```shell
locate chick
# /usr/share/vim/vim82/ftplugin/chicken.vim
# /usr/share/vim/vim82/syntax/chicken.vim
```

It will perform a search for all files that contain 'chick' in their name.

To update database use [updatedb](updatedb.md).

```shell
sudo updatedb
```

In Ubuntu `locate` command is not pre-installed. To install it use *apt* manager.

## Options

### -e, --existing

Print only entries that refer to files existing at the time `locate` is run.

Remember that `locate` uses a database file that it periodically updates. So if we
delete a file, it will keep in database and `locate` will return it. With `-e` option
it will return entries that only exist.

### -i, --ignore-case

Do a case-insensitive match (default case-sensitive, byte-by-byte match).

### -l, --limit LIMIT

Stop searching after LIMIT matches have been found.
