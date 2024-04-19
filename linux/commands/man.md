# man

Display the reference manual of the given command.

```shell
man ls
```

Press `q` to quit the manual. The manual opens in [less](less.md) editor.

In general, each man page will follow this pattern:

- The title/name of the command with a shot explanation of its purpose.
- Synopsis of the command's syntax.
- Description of the all the command's options.

You can get a listing of all the commands on your system that have a manual page by
entering:

```shell
man -k .
```

The resulting list a brief description of what each command does.

## man pages synopsis

Anything, listed inside square brackets is optional. The only required part from entire
line below is `ncal`.

```
ncal [-3bhjJpwySM] [-A number] [-B number] [-W number] [-s country_code] [[month] year]
```

The above synopsys tells us that we can use the following options without providing any
additional parameters: `-3`, `b`, `h`, `j`, `J`, `p`, `w`, `y`, `S` and `M`. To keep
things brief, they all lumped together as `[-3bhjJpwySM]`.

Option `[-A number]` expects a number parameter.

`[[month] year]` that means that we can pass month and year or just year as parameters.

---

Let's look at echo's synopsis:

```
echo [SHORT-OPTION]... [STRING]...
```

An ellipsis (`...`) indicates that one or more of the proceeding operands are allowed.
`[OPTION]...` means that we can pass more than one option to command.

`[STRING]...` indicates that we can pass multiple strings to `echo`.
