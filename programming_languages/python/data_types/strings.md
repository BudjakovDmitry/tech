# Strings

A string is a _sequence_ of characters.

You can specify strings using single quotes such as `'hello world'` or the double
quotes: `"What is your name?"`. Single and double quotes work exactly the same.

The reason of supporting both is that it allows you to embed a single-quote character in
a string enclosed in double-quote characters, and vice versa:

```python
s = 'knight"s', "knight's"
```

All white spaces i.e. spaces and tabs within the quotes are preserved as-is

```python
hello = "Hello world"
```

## String concatenation

```python
str_one = "Hello"
str_two = "World"
str_three = "!"

print(str_one + str_two + str_three)
# HelloWorld!

print(str_one + " " + str_two + str_three)
# Hello World!
```

Python automatically concatenates strig literals, divided by space. It is almost as
simple to add operator `+` between them.

```python
hello = "Hello" 'World'  # 'HelloWorld'

foo = (
    "Meaning"
    "Of"
    "Life"
)
print(foo)  # MeaningOfLife
```

## Escape Sequences

Backslashes are used to introduce special character codings known as _escape sequences_.

The character `\`, and one or more characters following it in the string literal, are
replaced with a _single_ character in the resulting string object, which has the binary
value specified by the escape sequence.

* `\n` new line;
* `\t` tab;

```python
s = 'Hello\nWorld\tBar'
```

## Methods

### str.find()

Basic substring search. It returns the offset of the passed-in substring or `-1` if it
is not present.

```python
s = 'spam'
s.find('pa')  # 1
```

### str.isalnum()

Return `True` if the string is an alpha-numeric string, False otherwise.

A string is alpha-numeric if all characters in the string are alpha-numeric and there is
at least one character in the string.

### str.lower()

Return a copy of the string converted to lowercase.

### str.split()

Split a string into substrings on a delimiter.

```python
line = 'aaa,bbb,cccc,dd'
line.split(',')
# ['aaa', 'bbb', 'cccc', 'dd']
```

The `split` method chops up a string into a list of substrings, around a delimiter
string. By default, delimiter is a whitespace - the string is split at groups of one or
more spaces, tabs and newlines.

```python
line = 'aaa bbb  ccc'
line.split()
# ['aaa', 'bbb', 'ccc']
```

### str.title()

Return a titlecased version of the string where words start with an uppercase character
and the remaining characters are lowercase.

```python
'Hello world'.title()  # 'Hello World'
```

The algorithm uses a simple language-independent definition of a word as groups of
consecutive letters. The definition works in many contexts, but it means that
apostrophes in contractions and possessives form word boundaries, which may not be the
desire result:

```python
"they're bill's friends from the UK".title()  # "They'Re Bill'S Friends From The Uk"
```

The `string.capwords()` function does not have this problem, as it splits words on
spaces only.

## String formatting

String formatting is available in three flavors:

* string formatting expressions;
* string formatting method calls;
* f-strings;

### String formatting expressions

The original technique available since Python's inception. This form is based upon the C
language's "printf" model. It is largely obsolete in modern Python.

### String formatting methods

```python
# By position
template = '{0}, {1} and {2}'
template.format('spam', 'ham', 'eggs')  # 'spam, ham and eggs'

# By keyword
template = '{motto}, {pork} and {food}'
template.format(motto='spam', pork='ham', food='eggs')  # 'spam, ham and eggs'

# By both
template = '{motto}, {0} and {food}'
template.format('ham', motto='spam', food='eggs')  # 'spam, ham and eggs'

# By relative position
template = '{}, {} and {}'
template.format('spam', 'ham', 'eggs')  # 'spam, ham and eggs'
```

Arbitrary object types can be substituted at targets:

```python
'{motto}, {0} and {food}'.format(42, motto=3.14, food=[1, 2])
# '3.14, 42 and [1, 2]'
```

As other string methods `format` method returns a new string object.

```python
x = '{motto}, {0} and {food}'.format(42, motto=3.14, food=[1, 2])
print(x)
# '3.14, 42 and [1, 2]'
```
