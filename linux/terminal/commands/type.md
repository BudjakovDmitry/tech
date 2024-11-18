# type

Print the type of command.

```shell
type clear  # clear is /usr/bin/clear
type type   # type is a shell builtin
type ls     # ls is aliased to `ls --color=auto'
```

There are really four types of commands:

- __An executable program__, usually stored in `/bin`, `/usr/bin` or `/usr/local/bin`. These
are compiled binary files such as programs written in C and C++, or programs written in
scripting languages such as shell, Perl, Python, Ruby and so on.
- __A built-in shell command__. These commands are part of the shell.
- __A shell function__. Shell functions are miniature shell scripts incorporated into
the environment.
- __An alias__.


