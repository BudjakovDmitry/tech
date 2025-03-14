# Packages and imports

## Packages

```
package main

import (
    "fmt"
    "math/rand"
)

func main() {
    fmt.Println("My favorite number is", rand.Intn(10))
}
```

Every Go program is made up of packages. There is a `package main` instruction at the
top of the code snippet. Every Go code file needs `package` instruction inside of it.

When you writing you program, you split your code across packages. You __must__ have at
least one package per application. But you can have multiple applications. And a single
package can be split across the multiple files.

The idea is behind all these packages is simply organize your code.

Program start running in package `main`. `main` is a special package name that tells Go,
that this package will be the main entry point of the application.

## Imports

Once we work with multiple packages, we can use features from package A in package B.
We can do it using `import` statement.

```
import (
    "fmt"
    "math"
)
```

This program is using the packages `"fmt"` and `"math"` by importing them.

Go comes with huge standard library of built-in packages.`"fmt"` package is a part of Go
Standard Library.

[Go Standard Library](https://pkg.go.dev/std)

By convention, the package name is the same as the last element of the import path. For
instance, the `"math/rand"` package comprises files that begin with the statement
`package rand`.

This code groups the imports into a parenthesized, "factored" import statement.

You can also write multiple import statements, like:

```
import "fmt"
import "math"
```

But it is a good style to use the factored import statement.

## Export names

In Go, a name is exported if it begins with a capital letter. For example, `Pizza` is an
exported name, as is `Pi`, which is exported from the `math` package.

`pizza` and `pi` do not start with a capital letter, so they are not exported.

When importing a package, you can refer only to its exported names. Any "unexported"
names are not accessible from outside the package.

```
package main

import (
    "fmt"
    "math"
)

func main() {
    fmt.Println(math.Pi)
}
```
