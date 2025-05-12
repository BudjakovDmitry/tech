# Enum

## Enum

An `Enum` is a set of symbolic names bound to unique values. They are similar to global
variables, but they offer a more useful `repr()`, grouping, type-safety, and few other
features.

They are most useful, when you have a variable that can take one of a limited selection
of values.

```python
from enum import Enum

class Weekday(Enum):
    MONDAY = 1
    TUESDAY = 2
    WEDNESDAY = 3
    THURSDAY = 4
    FRIDAY = 5
    SATURDAY = 6
    SUNDAY = 7
```

Creating an Enum is as simple as writing a class that inherits from `Enum` itself.

> __Note__: Because Enums are used to represent constants, and to help avoid issues with
> name clashes between mixin-class methods/attributes and enum names, documentation
> strongly recommends to use UPPER_CASE for members.

A member's value may or may not be important, but either way that value can be used to
get the corresponding member:

```python
# default __repr__
Weekday(3)  # <Weekday.WEDNESDAY: 3>

# default __str__
print(Weekday(3))  # Weekday.WEDNESDAY
```

```python
# type
type(Weekday.MONDAY)  # <enum 'Weekday'>

# isinstance
isinstance(Weekday.FRIDAY, Weekday)  # True
```

```python
# name and value
Weekday.TUESDAY.name  # 'TUESDAY'
Weekday.WEDNESDAY.value  # 3
```

Python Enums can have behaviour added. For example `datetime.date` has two methods for
returning the weekday: `weekday()` and `isoweekday()`. The difference is that one of
them counts from 0-6 and the other from 1-7. We can add a method to the `Weekday` enum
to extract the day from the `date` instance and return the matching enum member.

```python
import datetime
from enum import Enum

class Weekday(Enum):
    # ...

    @classmethod
    def from_date(cls, date: datetime.date):
        return cls(date.isoweekday())

Weekday.from_date(datetime.date.today())
```

## Programmatic access to enumeration members and their attributes

Sometimes it’s useful to access members in enumerations programmatically (i.e.
situations where `Color.RED` won’t do because the exact color is not known at
program-writing time). Enum allows such access:

```python
from enum import Enum

class Color(Enum):
    RED = 1
    GREEN = 2
    BLUE = 3

Color(1)
# <Color.RED: 1>
```

If you want to access enum members by name, use item access:

```python
Color["RED"]
# <Color.RED: 1>
```

## Comparisons

Enumeration members are compared by identity:

```python
Color.RED is Color.RED
# True

Color.RED is Color.BLUE
# False
```

Ordered comparisons between enumeration values _are not supported_ (explicitly `IntEnum`
):

```python
Color.RED < Color.BLUE
# TypeError: '<' not supported between instances of 'Color' and 'Color'
```

Equality comparisons are defined though:

```python
Color.BLUE == Color.RED
# False
```

Comparisons against non-enumeration values will always compare not equal (again,
`IntEnum` was explicitly designed to behave differently):

```python
Color.BLUE == 2
# False
```

> __Warning__: It is possible to reload modules – if a reloaded module contains enums,
> they will be recreated, and the new members may not compare identical/equal to the
> original members.

## StrEnum

`StrEnum` is the same as `Enum`, but ist members are also strings and can be used in
most of the same places that a string can be used. The result of any string operation
performed on or with a `StrEnum` member is not part of the enumeration.
