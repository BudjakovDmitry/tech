# Typing

## Variables

```python
# declare the type if a variable
age: int = 1

# You don't need to initialize a variable to annotate it
a: int  # Ok (no value at runtime until assigned)

# Doing so can be useful in conditional branches
child: bool
if age < 18:
    child = True
else:
    child = False
```

## Useful built-in types

For most types just use the name of the type in the annotation.

```python
x: int = 1
y: float = 1.0
is_admin: bool = True
t: str = "test"
tb: bytes = b"test"
```

Collections:

```python
x: list[int] = [1]
y: set[float] = {6, 7}
```

For mappings we need the type of both keys and values:

```python
x: dict[str, float] = {"field": 2.0}
```

For tuples of fixed size, we specify the types of all the elements

```python
x: tuple[int, str, float] = (3, "yes", 7.5)
```

For tuples of variable size, we use one type and ellipsis

```python
x: tuple[int, ...] = (1, 2, 3)
```

Use the `|` operator when something could be one of a few types (Python 3.10+). On
earlier versions use `Union`.

```python
# 3.10+
x: list[int | str] = [3, 6, "test", "fun"]

# 3.9 and earlier
from typing import Union
x: list[Union[int, str]] = [3, 5, "test", "fun"]
```

For a value that could be `None`:

```python
# 3.10+
x: str | None = "something" if some_condition() else None

# 3.9 and earlier
from typing import Optional
x: Optional[str] = "something" if some_condition() else None
```

## Functions

Annotate function definition.

```python
def stringify(num: int) -> str:
    return str(num)


def plus(num1: int, num2: int) -> int:
    return num1 + num2
```

If a function does not return a value, use `None` as the return type. Default value for
an argument goes after the type annotation.

```python
def show(value: str, excitement: int = 10) -> None:
    print(value + "!" * excitement)
```

This is how to annotate a callable (function) value

```python
from collections.abc import Callable

x: Callable[[int, float], float] = f

def register(callback: Callable[[str], int]) -> None:
    pass
```

A generator function that yields ints is secretly just a function that returns an
iterator of ints, so that's how we annotate it:

```python
from collections.abc import Iterator

def gen(n: int) -> Iterator[int]:
    i = 0
    while i < n:
        yield i
        i += 1
```

Splitting annotation over multiple lines:

```python
def send_email(
    addresses: str | list[str],
    sender: str,
    cc: list[str] | None,
    bcc: list[str] | None,
    subject: str = '',
    body: list[str] | None = None
) -> bool:
    pass
```

This says each positional arg and each keyword arg is a `str`:

```python
def call(self, *args: str, **kwargs: str) -> str:
    pass
```

## Classes

```python
class BankAccount:
    # The "__init__" method doesn't return anything, so type "None"
    def __init__(self, account_name: str, initial_balance: int = 0) -> None:
        self.account_name = account_name
        self.balance = initial_balance

    # for instance methods, omit type for "self"
    def deposit(self, amount: int) -> None:
        self.balance += amount

    def withdraw(self, amount: int) -> None:
        self.balance -= amount


# User-defined classes are valid as types in annotations
account: BankAccount = BankAccount("Alice", 400)

def transfer(src: BankAccount, dst: BankAccount, amount: int) -> None:
    src.withdraw(amount)
    dst.deposit(amount)

    
# Functions that accept BankAccount also accept any subclasses of BankAccount
class AuditedBankAccount(BankAccount):
    # You can optionally declare instance variables in the class body
    audit_log: list[str]

    def __init__(self, account_name: str, initial_balance: int = 0) -> None:
        super().__init__(account_name, initial_balance)
        self.audit_log: list[str] = []

    def deposit(self, amount: int) -> None:
        self.audit_log.append(f"Deposited {amount}")
        self.balance += amount

    def withdraw(self, amount: int) -> None:
        self.audit_log.append(f"Withdrew {amount}")
        self.balance -= amount

audited = AuditedBankAccount("Bob", 300)
transfer(audited, account, 100)
```

Use the ClassVar annotation to declare a class variable

```python
from typing import ClassVar

class Car:
    seats: ClassVar[int] = 4
    passengers: ClassVar[list[str]]
```

## Standard "duck types"

In typical Python code, many functions that can take a list or a dict as an argument
only need their argument to be somehow "list-like" or "dict-like". A specific meaning of
"list-like" or "dict-like" (or something-else-like) is called a "duck type", and several
duck types that are common in idiomatic Python are standardized.

Use `Iterable` for generic iterables (anything usable in "for"), and `Sequence` where
sequence (supporting `len` and `__getitem__`) is required.

```python
from collections.abc import  Iterable

def f(ints: Iterable[int]) -> list[str]:
    return [str(x) for x in ints]

f(range(1, 3))
```

`Mapping` describes a dict-like object (with "__getitem__") that we won't mutate, and
`MutableMapping` one (with "__setitem__") that we might:

```python
from collections.abc import Mapping, MutableMapping

def f(my_mapping: Mapping[int, str]) -> list[int]:
    return list(my_mapping.keys())

f({3: 'yes', 4: 'no'})


def f(my_mapping: MutableMapping[int, str]) -> set[str]:
    my_mapping[5] = "maybe"
    return set(my_mapping.values())

f({3: "yes", 4: "no"})
```

Use `IO[str]` or `IO[bytes]` for functions that should accept or return objects that
come from an `open()` call (`IO` does not distinguish between reading, writing or other
modes)

```python
import sys
from typing import IO


def get_sys_IO(mode: str = "w") -> IO[str]:
    if mode == "w":
        return sys.stdout
    elif mode == "r":
        return sys.stdin
    else:
        return sys.stdout
```

## Decorators

Example using Python 3.12 syntax:

```python
from collections.abc import Callable
from typing import Any


def bare_decorator[F: Callable[..., Any]](func: F) -> F:
    ...


def decorator_args[F: Callable[..., Any]](url: str) -> Callable[[F], F]:
    ...
```

The same example using pre-3.12 syntax:

```python
from collections.abc import Callable
from typing import Any, TypeVar

F = TypeVar("F", bound=Callable[..., Any])

def bare_decorator(func: F) -> F:
    ...

def decorator_args(url: str) -> Callable[[F], F]:
    ...
```

## Coroutines and asyncio

A coroutine is typed like a normal function.

```python
import asyncio

async def countdown(tag: str, count: int) -> str:
    while count > 0:
        print(f"T-minus {count} ({tag})")
        await asyncio.sleep(0.1)
        count -= 1
    return "Blastoff!"
```

## Type aliases

See PEP 695 for the `type` statement.

Type aliases may be defined by using the `type` statement (Python 3.12 and higher) which
creates an instance of `TypeAliasType`:

```python
type Url = str
def retry(url: Url, retry_count: int) -> None: ...
```

```python
type Vector = list[float]

def scale(scalar: float, vector: Vector) -> Vector:
    return [scalar * num for num in vector]

new_vector = scale(2.0, [1.0, -4.2, 5.4])
```

Python documentation [recommends](https://typing.python.org/en/latest/spec/aliases.html#type-aliases)
capitalizing alias names, since they represent user-defined types, which (like
user-defined classes) are typically spelled that way.

Type aliases are useful for simplifying complex type signatures. For example:

```python
from collections.abc import Sequence

type ConnectionOptions = dict[str, str]
type Address = tuple[str, int]
type Server = tuple[Address, ConnectionOptions]

def broadcast_message(message: str, servers: Sequence[Server]) -> None:
    ...

# The static type checker will treat the previous type signature as
# being exactly equivalent to this one
def broadcast_message(
    message: str,
    servers: Sequence[tuple[tuple[str, int], dict[str, str]]]
) -> None:
    ...
```

The `type` statement is new in Python 3.12. For backwards compatibility, type aliases
can also be created through simple assignment:

```python
Vector = list[float]
def scale(scalar: float, vector: Vector) -> Vector: ...
```
