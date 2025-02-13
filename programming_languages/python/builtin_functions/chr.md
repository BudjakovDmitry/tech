# chr

Return the string representing a character whose Unicode code point is the integer _i_.
This is inverse of `ord()`.

```python
chr(97)  # 'a'
chr(8364)  # '€'
```

The valid range of the argument is from 0 through 1,114,111 (0x10FFFF in base 16).
ValueError will be raised if _i_ is outside the range.
