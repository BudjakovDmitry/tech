# man

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

Let's look at echo's synopsis:

```
echo [SHORT-OPTION]... [STRING]...
```

An ellipsis (`...`) indicates that one or more of the proceeding operands are allowed.
`[OPTION]...` means that we can pass more than one option to command.

`[STRING]...` indicates that we can pass multiple strings to `echo`.
