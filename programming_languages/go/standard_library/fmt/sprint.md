# Sprint

Sprint formats using the default formats for its operands and returns the resulting
sprint. Spaces are added between operands when neither is a string.

```
package main

import "fmt"

func main() {
    const name, age = "Kim", 22
    s := fmt.Sprint(name, " is ", age, " years old.\n")
    fmt.Print(s)
}
```

Output:

```
Kim is 22 years old.
```
