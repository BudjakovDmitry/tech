# less

The `less` command is a program to view text files. It displays the file contents. You
can move around the file page-by-page (*Page Up*, *Page Down* keys) or line-by-line.

```shell
less /etc/passwd
```

The *less* programm was designed as an improved replacement of an earlier Unix program
called *more*. Unlike *more*, *less* does not automatically exit, when you reach the end
of a file, allowing you the option to continue scrolling around. Whereas the *more*
program could only page forward, the *less* program allows paging both forward and
backward.

The common keyboard commands used by *less*.

| Command | Action |
|---------|--------|
| Page Up or `b` | Scroll back one page |
| Page down or Space | Scroll forward one page |
| Up arrow | Scroll up one line |
| Down arrow | Scroll down one line |
| `G` | Move to the end of the text file |
| `g` | Move to the beginning of the text file |
| `/characters` | Search forward to the next occurrence of `characters` |
| `n` | Search for the next occurrence of the previous search |
| `h` | Display help screen |
| `q` | Quit *less* |

*Less* falls into the class of programs called *pagers*, programs that allow the easy
viewing of long text documents in a page-by-page manner.
