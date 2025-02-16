# info

`info` - display a program's info entry.

The GNU project provides an alternative to man pages for their programs, called `info`.
Info pages are hyperlinked much like web pages.

```shell
info ls
```

The `info` program reads info files, which are tree structured into individual nodes,
each containing a single topic. Info files contain hyperlinks that can move you from
node to node. A hyperlink can be identified by its leading asterisk and is activated by
placing the cursor upon it and pressing `ENTER`.

Below described the commands used to control the reader while displaying an info page.

* `?` Display command help;
* `PAGE UP` or `BACKSPACE` Display previous page;
* `PAGE DOWN` or `spacebar` Display next page;
* `n` Next - display the next node;
* `p` Previous - display the previous node;
* `U` Up - display the parent node of the currently displayed node, usually a menu;
* `ENTER` Follow the hyperlink at the cursor location;
* `Q` Quit;

```shell
info coreutils
```

will display a menu page with hyperlinks to each program contained in the coreutils
package.
