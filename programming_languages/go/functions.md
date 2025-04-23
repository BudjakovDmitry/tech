# Go functions

Function creates by using `func` keyword. The function body is enclosed in curly braces.

```
package main

import "fmt"

func sayHello() {
    fmt.Println("Hello world")
}

func main() {
    sayHello()
}
```

## Arguments

A function can take zero or more arguments.

```
package main

import "fmt"

// one argument
func sayHello(name string) {
    fmt.Printf("Hello %s\n", name)
}

// multiple arguments
func sayHelloFull(firstName string, lastName string) {
    fmt.Printf("Hello %s %s\n", firstName, lastName)
}

// zero arguments
func main() {
    firstName := "John"
    lastName := "Smith"
    sayHello(firstName)
    sayHelloFull(firstName, lastName)
}
```

When two or more consecutive named function parameters share a type, you can omit type
from all but the last.

In next example we shortened

```
func add(x int, y int)
```

to

```
func add(x, y int)
```

```
func add(x, y int) int {
    return x + y
}
```

## Return values

To return value from a function use `return` keyword. If a function return a value, you
have to define a type of returning value.

```
package main

import "fmt"

func add(x int, y int) int {
    return x + y
}

func main() {
    fmt.Println(add(42, 13))
}
```

A function can return any number of results split by the comma:

```
func swap(x, y string) (string, string) {
    return y, x
}

func main() {
    a, b := swap("hello", "world")
    fmt.Println(a, b)
}
```

Go's return values may be named. If so, they are treated as variables defined at the top
of the function.

These names should be used to document the meaning of the return values.

```
package main

import "fmt"

func split(sum int) (x, y int) {
    x = sum * 4 / 9
    y = sum - x
    return
}

func main() {
    fmt.Println(split(17))
}
```

A `return` statement without arguments returns the named return values. This is known as
a "naked" return. Naked return statements should be used only in short functions, as
with the example shown here. They can harm readability in longer functions.

## Function main

Any Go program that should be executable should have `main` function inside `main`
package. Go will call and execute that function when the program starts. Therefore, Go
program should have only one `main` function.

```
package main

import "fmt"

func main() {
    fmt.Print("Hello world")
}
```

If you're building third party library that exposes some utility functions, you don't
need to have `main` function.
