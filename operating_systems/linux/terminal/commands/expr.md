# expr

You can't execute math expression like `30 + 20` in bash. To do math bash has *evaluate
expression* command `expr`.

```shell
expr 30 + 20  # 50
expr 30 - 10  # 20
expr 40 / 20  # 2
```

Multiplication isn't work in straight way, because asterisk (`*`) symbol is a wildcard
that means everything in our current working directory.

We need to escape out the asterisk.

```shell
expr 10 \* 20
```

Example with variables:

```shell
num1=$100
num2=$20
expr $num1 + $num2  # 120  
```
