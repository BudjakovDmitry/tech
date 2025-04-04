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

* `\n` new line;

## Methods

### str.isalnum()

Return `True` if the string is an alpha-numeric string, False otherwise.

A string is alpha-numeric if all characters in the string are alpha-numeric and there is
at least one character in the string.

### str.lower()

Return a copy of the string converted to lowercase.

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

Added in Python 3.0
