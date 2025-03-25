# Variables

## Variable declaration

Go is a statically typed language. Every value has a specified type.

The `var` statement declares a list of variables. Variable names can contain only
letters, numbers and underscores. It may not start with a number. And you can not use
keyword as a variable name.

```
var name string
name = "Tim"
name = "Bill"
```

A `var` declaration can include initializers, one per variable. If an initializer is
present, the type can be omitted; the variable will take the type of the initializer.

```
var amount = 1000
var amount uint32 = 10000
var name string = "Tim"
var pi float64 = 3.14159

var i, j int = 1, 2
var c, python, java = true, false, "no!"
```

```
package main

import "fmt"

func main() {
  var investmentAmount = 1000
  var expectedReturnRate = 5.5
  var years = 10

  var futureValue = investmentAmount * (1 + expectedReturnRate / 100)
}
```

A `var` statement can be at package or function level.

```
package main

import "fmt"

var c, python, java bool

func main() {
    var i int
    fmt.Println(i, c, python, java)
}
```

## Short variable declaration

Inside a function (even the main function), the `:=` short assignment statement can be
used in place of a `var` declaration. The `:=` operator infers the type of the new
variable based on the value.

```
var empty string
```

is the same as

```
empty := ""
```

```
numCars := 10  // inferred to be integer
temperature := 0.0  // inferred to be a floating point
name, age, likesGo := "Jeff", 75, true
```
