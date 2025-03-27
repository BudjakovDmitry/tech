# print

`print` is simply a programmer-friendly interface to the standard output stream.

Technically, printing converts one or more objects to their textual representations,
adds some minor formatting, and sends the resulting text to either standard output or
another file-like stream.

Print does not return any value (technically, it returns `None`).

```python
print('Hello world')
```

Call format:

```
print([object, ...][, sep=' '][, end='\n'][, file=sys.stdout][, flush=False])
```

* `sep` is a string inserted between each object's text. `' '` by default.
* `end` is a string added at the end of the printed text; `\n` by default.
* `file` specifies the file, standard stream, or other file-like object to which the
text will be sent. `sys.stdout` by default. Any object with a file-like `write(string)`
method may be passed.
* `flush` allows prints to mandate that their text be flushed through the output stream
immediately to any waiting recipients. Normally, whether printed output is buffered in
memory or not is determined by file; passing a `True` value to flush forcibly flushes
the stream. `False` by default.

This built-in function prints the textual representation of one or more `objects`
separated by the string `sep` and followed by the string `end` to the stream `file`,
flushing buffered output or not per `flush`.

`sep`, `end`, `file` and `flush` parts, if present, must be given as _keyword
arguments_.

The textual representation of each `object` to be printed is obtained by passing the
object to the `str` built-in call. This built-in returns a “user friendly” display
string for any object. With no arguments at all, the print function simply prints a
newline character to the standard output stream, which usually displays a blank line.
