# Decorators

- *Function decorators* specify special operation modes for both simple functions and
classes' methods by wrapping them in an extra layer of logic implemented as another
function, usually called *metafunction*.
- *Class decorators* do the same for classes, adding support for management of whole
objects and their interfaces.

# Function decorator

A function decorator is coded just before the `def` statement that defines a function or
method. It consists of the `@` symbol, followed by that we call a *metafunction* - a
function (or other callable function) that manages another function.

```python
@decorator  # function decorator syntax
def say_hello():
    print("Hello")
```

Internally, this syntax has the same effect as the following - passing the function
through the decorator and assigning the result back to the original name.

```python
say_hello = decorator(say_hello)
```
