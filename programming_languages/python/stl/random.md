# random - Generate pseudo-random numbers

## Functions for integers

### random.randrange(stop), random.randrange(start, stop\[, step\])

Return a random selected element from `range(start, stop, step)`.

This is roughly equivalent to `choice(range(start, stop, step))` but supports arbitrary
large ranges and is optimized for common cases.

For positional arguments pattern matches the `range()` function.

Keyword arguments should not be used because they can be interpreted in unexpected ways.
For example `randrange(start=100)` is interpreted as `randrange(0, 100, 1)`

Automatic conversion of non-integer types in not supported in version 3.12.
Calls such `randrange(10.0)` and `randrange(Fraction(10, 1))` raise `TypeError`

### random.randint(a, b)

Return a random integer _N_ such that `a <= N <= b`. Alias for `randrange(a, b+1)`

## Functions for sequences

### random.choice(seq)

Return a random element from the non-empty sequence `seq`. If `seq` is empty, raises
`IndexError`.

## Real-valued distributions

### random.random()

Return the next random floating-point number in the range `0.0 <= X < 1.0`

```python
import random

print(random.random())  # 0.6978432774493304
```
