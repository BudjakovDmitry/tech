# less

The `less` command is a program to view text files. It displays the file contents. You
can move around the file page-by-page or line-by-line.

```shell
less /etc/passwd
```

The *less* program was designed as an improved replacement of an earlier Unix program
called *more*. Unlike *more*, *less* does not automatically exit, when you reach the end
of a file, allowing you the option to continue scrolling around. Whereas the *more*
program could only page forward, the *less* program allows paging both forward and
backward.

The common keyboard commands used by *less*. To find all commands type `h`.

| Command                   | Action |
|---------------------------|--------|
| Page Up or `b`            | Scroll back one page |
| Page down or Space or `f` | Scroll forward one page |
| Up arrow                  | Scroll up one line |
| Down arrow or Enter       | Scroll down one line |
| `G`                       | Move to the end of the text file |
| `g`                       | Move to the beginning of the text file |
| `/characters`             | Search forward to the next occurrence of `characters` |
| `n`                       | Search for the next occurrence of the previous search |
| `h`                       | Display help screen |
| `q`                       | Quit *less* |

*less* falls into the class of programs called *pagers*, programs that allow the easy
viewing of long text documents in a page-by-page manner.
