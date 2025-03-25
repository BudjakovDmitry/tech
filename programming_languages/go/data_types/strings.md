# Strings

To create string value use double quotes: `fmt.Print("Hello world")`. It is also
available to use backticks. It is not allowed to use single quotes to create strings in
Go.

```
var name string = "Sam"
```

## Formatting strings

```
package main

import "fmt"

func main() {
    value := 2
    fmt.Printf("The type of value is %T\n", value)
}
```

`%T` tells to print type of the variable rather than its value.
