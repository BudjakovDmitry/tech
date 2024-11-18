# alias

We can create a commands for our own using the `alias` command.

The first thing we have to do is dream up a name for a new command. After that is a good
idea to find out whether the name is already being used. To find out we can use the
`type` command.

```shell
type my_new_awesome_command
```

The structure of `alias`:

```shell
alias name='string'
```

```shell
alias foo='cd /usr; ls; cd -'
```

After the command `alias`, we give our alias a name followed immediately by an equal
sign (no whitespace allowed), followed immediately by a quoted string containing the
meaning to be assigned to the name. After we define an alias, we can use it anywhere the
shell would expect a command.

```shell
foo
type foo
```

To remove an alias the [`unalias`](unalias.md) command is used.

To see all aliases defined in the environment, use the `alias` command without
arguments.
