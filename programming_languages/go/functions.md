# Go functions

A function can take zero or more arguments.

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

In this example, `add` takes two parameters of type `int`.

Type comes _after_ the variable name.

When two or more consecutive named function parameters share a type, you can omit type
from all but the last.

In next example we shortened

```
x int, y int
```

to

```
x, y int
```

```
func add(x, y int) int {
    return x + y
}
```

A function can return any number of results:

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

A `return` statement without arguments returns the named return values. This is known as
a "naked" return. Naked return statements should be used only in short functions, as
with the example shown here. They can harm readability in longer functions.

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
