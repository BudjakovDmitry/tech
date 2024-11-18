# man

Display the reference manual of the given command.

Most executable programs intended for command line use provide a formal piece of
documentation called *manual*.

```shell
man ls
```

The manual opens in [less](less.md) editor. Press `q` to quit the manual.

Not every command has a manual page, especially if we talk about built-in shell
commands. In that case use [help](help.md) command.

In general, each man page will follow this pattern:

- The title/name of the command with a shot explanation of its purpose.
- Synopsis of the command's syntax.
- Description of the all the command's options.

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

## Manual sections

The manual is broken into 8 different sections, each covering a specific topic in depth:

1. Executable programs or shell commands
2. System calls (functions provided by the kernel)
3. Library calls (functions within program libraries)
4. Special files (usually found in `/dev`)
5. File forms and conversations, e.g. `/etc/passwd`
6. Games
7. Miscellaneous (including macro packages and conventions)
8. System administration commands (usually only for root)
9. Kernel routines [Not standard]

Sometimes we need to refer to a specific section of the manual. This is particularly
true, if we are looking for a file format that is also a name of a command. Without
specifying a section number, we will always get the first instance of a match, probably
in section 1. To specify a section number, use `man` like this

```shell
man section search_term

# display the man page describing the file format of the /etc/passwd file
man 5 passwd
```

## Options

### -k

```shell
man -k copy
```

Search the short descriptions and manual page names for the keyword `copy` as regular
expression. Print out any matches. The example above prints out something like:

```
...
bcopy (3)            - copy byte sequence
cp (1)               - copy files and directories
COPY (7)             - copy data between a file and a table
...
```

`bcopy` is a function from section 3 (library calls), `cp` is a shell command from
section 1, `COPY` is a command from PostgreSQL documentation (section 7).

We can get a manual for each of these entities: `man bcopy` or `man cp` or `man COPY`,
etc.

Sometimes there are the same names for commands from different sections, for exemple

```shell
man -k passwd
```

```
...
passwd (1)           - change user password
passwd (5)           - the password file
...
```

By default, command `man passwd` prints manual for util *passwd* from section 1. If we
want to read manual for *passwd* from section 5 we should print `man 5 passwd`.

You can get a listing of all the commands on your system that have a manual page by
entering:

```shell
man -k .
```

The resulting list a brief description of what each command does.
