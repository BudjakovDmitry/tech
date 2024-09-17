# Arithmetic expansion

The shell performs arithmetic via expansion using the `$((math_expression))` syntax.
Inside the parentheses, we can write arithmetic expressions using:

* `+` addition
* `-` subtraction
* `*` multiplication
* `/` division
* `**` exponentation
* `%` modulo (remainder operator)

```shell
echo $((10+7))
# 17

echo $((10-3))
# 7

echo $((3*13))
# 39

echo $((2**10))
# 1024

echo $((10%3))
# 1
```

The shell only performs integer arithmetic, so the result is always an integer number.

```shell
echo $((10/3))
# 3
```

We can use more complicated expressions and use parentheses to change the order.

```shell
echo $((5+4*2))
# 13

echo $(((5+4)*2))
# 18
```
