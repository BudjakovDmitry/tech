# Terminal commands history

If we press the up arrow, we will see that the previous command entered. This is called
command history. Press the down arrow and the previous command disappears.

Use [history](commands/history.md) command to view the entire history.

Bash keeps history in the file `~/.bash_history`.

## History expansion

We can re-run an earlier command if we have its line from the history. For example:

```shell
!273
```

## Searching history

Often it is easier to find and earlier command by searching using a small portion of the
command that you remember.

Type `Ctrl - r` to enter "reverse-i-search". As you start typing, bash will search the
history and show you the best match. If you want to run the command, hit enter.

Hit `Ctrl - r` to cycle through potential matches.

## Limits

Most Linux distributions remember the last 1,000 commands by default. User can change
this limit.

Print how many commands the *.bash_history* file will store.

```shell
echo $HISTFILESIZE
```

Print how many commands will sored in memory in current session.

```shell
echo $HISTSIZE
```
