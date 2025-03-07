# Packages

Every Go program is made up of packages.

Program start running in package `main`.

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

This program is using the packages with imports `"fmt"` and `"math/rand"`.

By convention, the package name is the same as the last element of the import path. For
instance, the `"math/rand"` package comprises files that begin with the statement
`package rand`.
