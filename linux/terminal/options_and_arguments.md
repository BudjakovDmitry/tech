# Options and Arguments

Commands are often followed by one or more *options* that modify their behavior and,
further, by one or more *arguments*. So, most commands look kind of like this:

```
command -options arguments
```

Most commands use options, which consists of a single character preceded by a dash, for
example (`-l`). Many commands, however, including those from the GNU Project, also
support *long options*, consisting of a word preceded by two dashes. Also, many commands
allow multiple short options to be strung together.

```shell
ls -lt
```

But we can't collapse long options:

```shell
sort colors.txt --reverse --unique
```

Command options, like filenames in Linux, are case-sensitive.

Some options require us to pass in an additional value. For example:

```shell
ncal -A 2
# or
ncal -A2
```

You can add space between option and value or not. Both commands `ncal -A 2` and
`ncal -A2` are correct and return the same result.

If we have options that expect a value to be passed, we need to provide other option
separately. For example:

```shell
ncal -B1 -M
```

Usually you don't have to put options before the arguments, but it is pretty common to
do it that way. So, put your options before the arguments.
