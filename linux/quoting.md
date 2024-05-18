# Quoting

The shell performs something called word splitting.

```shell
echo I     love       spaces
# I love spaces
```

In next example shell thinks we are referencing a variable called *hit*. It can't find
a value of *hit*, so it substitutes an empty string instead.

```shell
echo holy $hit
# holy
```

## Double quotes

If we wrap text in double quotes, the shell will respect our spacing and will ignore
special characters **except** for
- dollar sign ($)
- backslash (\\)
- backtick (\`)

```shell
echo Hello     World
# Hello World

echo "Hello     World"
# Hello     World
```

Pathname expansion, brace expansion, and word splitting will be ignored. However,
command substitution and arithmetic expansion is still performed because dollar signs
still have meaning inside double quotes.

```shell
echo {1..9}
# 1 2 3 4 5 6 7 8 9

echo "{1..9}"
# {1..9}

# dollar sign still have its meaning inside double quotes
echo "5 + 5 =      $((5+5))"
# 5 + 5 =      10
```

## Single quites

Use single quotes to suppress all forms of substitution.

```shell
echo '5 + 5 =       $((5+5))'
# 5 + 5 =       $((5+5))
```
