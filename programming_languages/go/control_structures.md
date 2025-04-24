# Control structures

## if statement

```
if isAdmin(userId) {
    // some code here
}
```

* AND - `&&`
* OR - `||`

```
if userChoice == "pause" {
    // some code here
} else if userChoice == "continue" {
    // some code here
} else {
    // some code here
}
```

If variable was defined within `if` branch, it is scoped inside this branch and nowhere
else.

```
if isAdmin(userId) {
    var message string
    // `message` available only in this branch
}
// here variable `message` is not available
```
