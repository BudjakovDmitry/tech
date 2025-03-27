# sys

## stdin, stdout, stderr

File objects used by the interpreter for standard input, output and errors:

* `stdin` is used for all interactive input (including calls to `input()`);
* `stdout` is used for the output of `print()` and expression statements and for the
prompts of `input()`;
* The interpreter’s own prompts and its error messages go to `stderr`.

These streams are regular text files like those returned by the `open()` function.
