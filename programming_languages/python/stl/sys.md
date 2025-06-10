# sys

## getrefcount(object)

Return the reference count of the object. The count returned is generally one higher
than you might expect, because it includes the (temporary) reference as an argument to
`getrefcount()`.

Note that the returned value may not actually reflect how many references to the object
are actually held. For example, some objects are immortal and have a very high refcount
that does not reflect the actual number of references. Consequently, do not rely on the
returned value to be accurate, other than a value of 0 or 1.

> If an object is _immortal_, its reference count is never modified, and therefore it is
> never deallocated while the interpreter is running. For example, `True` and `None` are
> immortal in CPython.
>
> Immortal objects are a CPython implementation detail introduced in PEP 683.

## stdin, stdout, stderr

File objects used by the interpreter for standard input, output and errors:

* `stdin` is used for all interactive input (including calls to `input()`);
* `stdout` is used for the output of `print()` and expression statements and for the
prompts of `input()`;
* The interpreter’s own prompts and its error messages go to `stderr`.

These streams are regular text files like those returned by the `open()` function.
