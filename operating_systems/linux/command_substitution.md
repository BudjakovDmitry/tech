# Command substitution

We can use the `$(command)` syntax to display the output of the command. It can be very
useful when you write shell scripts.

```shell
echo today is $(date)
# today is Tue May 21 07:12:16 AM IDT 2024

echo Hi, I am $(whoami)
# Hi, I am john
```

Alternative syntax for the command substitution:

```shell
echo I am `whoami`
# I am john
```
