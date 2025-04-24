# Loops

There is only one type of loop you can create in Go: `for` loop.

First option:

```
for i := 0; i < 10; i++ {
    // loop body will execute as long as i < 10 in this case
}
```

Conditional loop:

```
for someCondition {
    // do something...
```

`someCondition` is an expression that yields a boolean value or a variable that contains
a boolean value. In that case, the loop will continue to execute the code inside the
loop body until the condition / variable yields `false`.

Infinite loop:

```
for {
    // this loop will execute forefer
}
```

`break` keyword brake us out of the loop.

`continue` keyword starts the new iteration.
