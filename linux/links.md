# Hard links, Symbolic links

To create hard links or symbolic links use [ln](/linux/commands/ln.md) command.

## Symbolic link

Symbolic link works by creating a special type of file that contains a text pointer to
the referenced file or directory. The symbolic link and file it points to have different
inode numbers because symbolic link and a file it links to are completely different
objects.

## Hard link

By default, every file has a single hard link that gives the file its name.

Hard links are the original Unix way of creating links. Modern practice prefers symbolic
links.

Hard links have two important limitations:

- A hard link cannot reference a file outside its own file system. This means a link
cannot reference a file that is not on the same disk partition as the link itself. It
because inode number will have absolutely different meaning in the other file system.
- A hard link may not reference a directory.

A hard link is indistinguishable from the file itself. Unlike a symbolic link, when you
list a directory containing a hard link, you will see no special indication of the link.
When a hard link is deleted, the link is removed, but the contents of the file itself
continue to exist until all links to the file are deleted.

Hard links which point to the same file have the same inode number. When we create a
hard link we create an additional entry to a file. Each hard link refers to a specific
inode containing the file's contents.
