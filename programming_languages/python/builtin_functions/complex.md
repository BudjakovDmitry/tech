# complex

```python
complex(real=10, imag=2)  # (10+5j)
complex("20+8j")  # (20+8j)
complex(5, 8)
# (5+8j)
```

Return a complex number with the value _real + imag*1j_ or convert a string or number to
a complex number. If the first parameter is a string, it will be interpreted as a
complex number and a function must be called without second parameter. The second
parameter can never be a string. Each parameter may be any numeric type (including
complex). If _imag_ is omitted, it defaults to zero and the constructor serves as a
numeric conversion like `int` and `float`. If both parameters are omitted, returns `0j`.

For a general Python object `x`, `complex(x)` delegates to `x.__complex__()`. If
`__complex__()` is not defined then it falls back to `__float__()`. If `__float__()` is
not defined then falls back to `__index__()`.
