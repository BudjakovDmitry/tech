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

## switch statement

```
var userChoice string
userChoice = getUserChoice()

switch userChoice {
case "pause":
  // do some code
case "continue":
  // some code
  // more code
  // multiple lines
default:
  // if no options above were selected
}
```

In `switch` `break` keyword has a special meaning. It is no longer breaks closest
surrounding loop. Inside `switch` construction `break` keyword breaks current switch
branch. That is why you should be careful using `switch` inside a loop.
