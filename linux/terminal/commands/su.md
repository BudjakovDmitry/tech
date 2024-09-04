# su

su stands for substitute user.

There may be times we want to start a shell as another user, from within our own shell
session. Basically switch to another user, but without having to log out and log back in
as that user.

```shell
# create a new login shell for the user harry.
su --login harry
```

To leave the session, type `exit`.

For backward compatibility, `su` defaults not to change the current directory and to
only set the environment variables `HOME` and `SHELL` (plus `USER` and `LOGNAME` if the
target user is not root). It is recommended to always use the `--login` option (instead
of its shortcut `-`) to avoid side effects caused by mixing environments.
