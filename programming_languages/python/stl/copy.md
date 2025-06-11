# Copy

## copy.copy(obj)

Return a shallow copy of `obj`.

```python
import copy

numbers = [1, 2, 3]
copy.copy(numbers)  # return [1, 2, 3]
```

## copy.deepcopy(obj[, memo])

Return a deep copy of `obj`.

```python
import copy

persons = [{'name': 'John', 'age': 25}, {'name': 'Jane', 'age': 22}]
persons_copied = copy.deepcopy(persons)
```

The difference between shallow and deep copying is only relevant for compound objects
(objects that contain other objects, like lists or class instances):

* A _shallow_ copy constructs a new compound object and then (to the extent possible)
inserts _references_ into it to the objects found in the original.
* A _deep copy_ constructs a new compound object and then, recursively, inserts _copies_
into it of the objects found in the original.
