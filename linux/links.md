# Hard links, Symbolic links

To create hard links or symbolic links use [ln](terminal/commands/ln.md) command.

## Symbolic link

Symbolic links also known as _soft links_ or _symlinks_.

Symbolic link works by creating a special type of file that contains a text pointer to
the referenced file or directory. The symbolic link and file it points to have different
inode numbers because symbolic link and a file it links to are completely different
objects. But a file pointed to by a symbolic link and the symbolic link itself are
largely indistinguishable from one another. For example, if you write something to the
symbolic link, the referenced file is written to. When you delete a symbolic link,
however, only the *link* is deleted, not the *file* itself. If the file is deleted
before the symbolic link, the link will continue to exist but will point to nothing. In
this case the link is said to be *broken*.

The symbolic links looks like this:

```shell
lrwxrwxrwx 1 root root 11 2024-11-08 14:38 libc.so.6 -> libc-2.6.so
```

The first letter of the listing is `l`. The symbolic link called `libc.so.6` and it points
to a shared library file called `lib-2.6.so`. This means, that programs looking for
`lib.so.6` will actually get the file `lib-2.6.so`.

Scenario of usage symlinks: a program requires the use of a shared file named "foo", but
"foo" has frequent version changes. It would be good to include the version number in
the filename so the administrator could see what version of "foo" is installed. This
presents a problem. If we change the name of the shared resource, we have to track down
every program that might use it and change it to look for a new resource name every time
a new version of resource is installed.

Here is where symbolic links help. Suppose we install version 2.6 of "foo", which has
filename "foo-2.6", and then create a symbolic link simply called "foo" that points to
"foo-2.6". This means that when a program opens file "foo", it is actually opening the
file "foo-2.6". The program that rely on "foo" can find it, and we can still see what
actual version is installed. When it is time to upgrade to "foo-2.7", we just add the
file to our system, delete the symbolic link "foo", and create a new one that points to
the new version. This approach also allows us to keep both versions on our machine.
Imagine we need to revert to the old version. We just delete the symbolic link pointing
to the new version and create a new symbolic link pointing to the old version.

## Hard link

There is a second type of link called _hard links_. Hard links also allow files to have
multiple names, but they do it in a different way.

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
continue to exist until all links to the file are deleted. So how do we know, that two
links in fact are the same file?

When thinking about hard links, it is helpful to imagine that files are made up of two
parts:

* The data part containing the file's contents;
* The name part that holds the file's name;

When we create hard links, we actually creating additional name parts that all refer
to the same data part. The system assigns a chain of disk blocks to what we called an
*inode*, which is then associated with the name part. Each hard link therefore refers
to a specific inode containing the file's contents. To find out an inode use `ls -i`.

Hard links which point to the same file have the same inode number. When we create a
hard link we create an additional entry to a file. Each hard link refers to a specific
inode containing the file's contents.
