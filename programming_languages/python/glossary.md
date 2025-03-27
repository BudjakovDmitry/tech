# Glossary

## file object

An object exposing a file-oriented API (with methods such as `read()` or `write()`) to
an underlying resource. Depending on the way it was created, a file object can mediate
access to a real on-disk file or to another type of storage or communication device (for
example standard input/output, in-memory buffers, sockets, pipes, etc.). File objects
are also called _file-like objects_ or _streams_.

There are actually three categories of file objects:

* raw binary files,
* buffered binary files
* text files.

Their interfaces are defined in the `io` module. The canonical way to create a file
object is by using the `open()` function.