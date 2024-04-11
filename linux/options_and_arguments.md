# Options and Arguments

Commands are often followed by one or more *options* that modify their behavior and,
further, by one or more *arguments*. So, most commands look kind of like this:

```
command -options arguments
```

Most commands use options, which consists of a single character preceded by a dash, for
example (`-l`). Many commands, however, including those from the GNU Project, also
support long options, consisting of a word preceded by two dashes. Also, many commands
allow multiple short options to be strung together.

```shell
ls -lt
```

Command options, like filenames in Linux, are case sensitive.
