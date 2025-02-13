# Exceptions

## Built-in Exceptions

Exception hierarchy:

<pre>
BaseException
 ├── BaseExceptionGroup
 ├── GeneratorExit
 ├── KeyboardInterrupt
 ├── SystemExit
 └── Exception
     ├── ArithmeticError
     │    ├── FloatingPointError
     │    ├── OverflowError
     │    └── ZeroDivisionError
     ├── AssertionError
     ├── AttributeError
     ├── BufferError
     ├── EOFError
     ├── ExceptionGroup [BaseExceptionGroup]
     ├── ImportError
     │    └── ModuleNotFoundError
     ├── LookupError
     │    ├── IndexError
     │    └── KeyError
     ├── MemoryError
     ├── NameError
     │    └── UnboundLocalError
     ├── OSError
     │    ├── BlockingIOError
     │    ├── ChildProcessError
     │    ├── ConnectionError
     │    │    ├── BrokenPipeError
     │    │    ├── ConnectionAbortedError
     │    │    ├── ConnectionRefusedError
     │    │    └── ConnectionResetError
     │    ├── FileExistsError
     │    ├── FileNotFoundError
     │    ├── InterruptedError
     │    ├── IsADirectoryError
     │    ├── NotADirectoryError
     │    ├── PermissionError
     │    ├── ProcessLookupError
     │    └── TimeoutError
     ├── ReferenceError
     ├── RuntimeError
     │    ├── NotImplementedError
     │    ├── PythonFinalizationError
     │    └── RecursionError
     ├── StopAsyncIteration
     ├── StopIteration
     ├── SyntaxError
     │    └── IndentationError
     │         └── TabError
     ├── SystemError
     ├── TypeError
     ├── ValueError
     │    └── UnicodeError
     │         ├── UnicodeDecodeError
     │         ├── UnicodeEncodeError
     │         └── UnicodeTranslateError
     └── Warnings
          ├── BytesWarning
          ├── DeprecationWarning
          ├── EncodingWarning
          ├── FutureWarning
          ├── ImportWarning
          ├── PendingDeprecationWarning
          ├── ResourceWarning
          ├── RuntimeWarning
          ├── SyntaxWarning
          ├── UnicodeWarning
          └── UserWarning
</pre>

### IndexError

Raised when a sequence subscript is out of range. (Slice indices are silently truncated
to fall in the allowed range). If an index is not an integer, `TypeError` is raised.

### ValueError

Raised when an operator or function receives an argument that has the right type but an
inappropriate value, and the situation is not described by a more precise exception
such as `IndexError`.

### ZeroDivisionError

Raised when the second argument of a division or modulo operation is zero. The
associated value is a string indicating the type of the operands and the operation.
