# sudo

This command allows us to run other commands as the root user.

```shell
sudo apt update
```

By default, Ubuntu disables logins to the root account. Instead, the initial user is
granted full access to all superuser privileges. We can run specific commands as the
root user by using `sudo` command.

Individual users are granted an "allowed" list of commands they can run as the
superuser.

Not every user can run commands with `sudo`. 

## Options

### -l, --list

If no command is specified, list the allowed (and forbidden) commands for the invoking
user (or the user specified by the `-U` option) on the current host.
