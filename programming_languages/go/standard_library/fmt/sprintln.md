# Sprintln

```
func Sprintln(a ...any) string
```

Sprintln formats using the default formats for its operands and returns the resulting
string. Spaces are always added between operands and a newline is appended.

```
package main

import "fmt"

func main() {
    const name, age = "Kim", 22
    s := fmt.Sprintln(name, "is", age, "years old.")
    fmt.Print(s)
}
```

Output:

```
Kim is 22 years old.
```
