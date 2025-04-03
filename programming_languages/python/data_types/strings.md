# Strings

A string is a _sequence_ of characters.

You can specify strings using single quotes such as `'hello world'` or the double
quotes: `"What is your name?"`. Single and double quotes work exactly the same.

All white spaces i.e. spaces and tabs within the quotes are preserved as-is

```python
"Hello world"
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

## Escape Sequences

* `\n` new line;

## Methods

### str.isalnum()

Return `True` if the string is an alpha-numeric string, False otherwise.

A string is alpha-numeric if all characters in the string are alpha-numeric and there is
at least one character in the string.

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
