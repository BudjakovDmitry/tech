# Integers numbers

```python
a = 10
b = 0b0101101  # literal in binary form
c = 1_234_567  # separators
d = 0xfff15a   # hexadecial form
```

For large numbers Python automatically provides extra precision.

```python
large_number = 2 ** 10000
```

> Python integers can be arbitrarily large and may even be used to represent
> floating-point values with extended precision. While integer size is limited only by
> your computer’s memory, though, Python 3.11 and later require extra steps to convert
> pathologically large numbers to decimal strings (e.g., for str or display). This
> avoids rare denial-of-service attacks with a 4,300-digit limit that can be lifted with
> a `sys` module tool, `set_int_max_str_digits`; call this to count digits in larger
> numbers.


