# id

Return the “identity” of an object. This is an integer which is guaranteed to be unique
and constant for this object during its lifetime. Two objects with non-overlapping
lifetimes may have the same `id()` value.

__CPython implementation detail__: This is the address of the object in memory.

```python
id("Hello world")  # 124255364814640
```
