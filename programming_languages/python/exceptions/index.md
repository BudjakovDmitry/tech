# Exceptions

## Built-in Exceptions

### IndexError

Raised when a sequence subscript is out of range. (Slice indices are silently truncated
to fall in the allowed range). If an index is not an integer, `TypeError` is raised.

### ValueError

Raised when an operator or function receives an argument that has the right type but an
inappropriate value, and the situation is not described by a more precise exception
such as `IndexError`.
