# bin

Convert an integer number to a binary string prefixed with "0b". The result is a valid
Python expression. If _x_ is not a Python _int_ object, it has to define an
`__index__()` method that returns an integer.

```python
bin(42)   # '0b101010'
bin(-10)  # '-0b1010'


class Foo:
    def __index__(self):
        return 100

foo = Foo()
bin(foo)  # '0b1100100'
```
