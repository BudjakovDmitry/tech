# Sequences

Sequence is a positionally oriented collection of other objects. Sequences maintain a
left-to-right order among the items they contain: their items are stored and fetched by
their relative positions.

Sequence examples: _lists_, _strings_, _tuples_.

## Operations with sequences

### Indexing

```python
s = "Spam"
s[0]  # 'S'
s[1]  # 'p'
```

In Python, indexes are coded as offers from the front, and so start from 0: the first
item is at index 0, second at index 1, and so on.

We can use negative indexes. Negative indexes count back from the right:

```python
s = "Spam"
s[-1]  # 'm'
s[-2]  # 'a'
```

### Slicing

```python
s = "Spam"
s[1:3]  # 'pa'
```

`x[i:j]` means: "give me everything in `x` from the offset `i` up to but not including
offset `j`".

```python
s[1:]  # 'pam'
s[0:3]  # 'Spa'
s[:3]  # 'Spa'
s[:-1]  # 'Spa'
s[:]  # 'Spam'
```
