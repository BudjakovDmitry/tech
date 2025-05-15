# Typing

## typing.Annotated


Special typing form to add context-specific metadata to an annotation.

Add metadata `x` to a given type `T` by using the annotation `Annotated[T, x]`. Metadata
added using `Annotated` can be used by static analysis tools or at runtime. At runtime,
the metadata is stored in a `__metadata__` attribute.

If a library or tool encounters an annotation `Annotated[T, x]` and has no special logic
for the metadata, it should ignore the metadata and simply treat the annotation as `T`.
As such, `Annotated` can be useful for code that wants to use annotations for purposes
outside Python’s static typing system.

Using `Annotated[T, x]` as an annotation still allows for static typechecking of `T`, as
type checkers will simply ignore the metadata `x`. In this way, `Annotated` differs from
the `@no_type_check` decorator, which can also be used for adding annotations outside
the scope of the typing system, but completely disables typechecking for a function or
class.

The responsibility of how to interpret the metadata lies with the tool or library
encountering an `Annotated` annotation. A tool or library encountering an `Annotated`
type can scan through the metadata elements to determine if they are of interest (e.g.,
using `isinstance()`).

```python
# using Annotated to range analysis
@dataclass
class ValueRange:
    lo: int
    hi: int

T1 = Annotated[int, ValueRange(-10, 5)]
T2 = Annotated[T1, ValueRange(-20, 3)]
```

The first argument to Annotated must be a valid type.

Multiple metadata elements can be supplied as `Annotated` supports variadic arguments.
The order of the metadata elements is preserved and matters for equality checks:

```python
@dataclass
class ctype:
     kind: str

a1 = Annotated[int, ValueRange(3, 10), ctype("char")]
a2 = Annotated[int, ctype("char"), ValueRange(3, 10)]

assert a1 != a2  # Order matters
```

It is up to the tool consuming the annotations to decide whether the client is allowed
to add multiple metadata elements to one annotation and how to merge those annotations.

Nested Annotated types are flattened. The order of the metadata elements starts with the
innermost annotation:

```python
assert (
        Annotated[Annotated[int, ValueRange(3, 10)], ctype("char")] ==
        Annotated[int, ValueRange(3, 10), ctype("char"))]
)
```

However, this does not apply to `Annotated` types referenced through a type alias, to
avoid forcing evaluation of the underlying TypeAliasType:
