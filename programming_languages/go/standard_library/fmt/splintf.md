# Splintf

```
func Splintf(format string, a ...any) string
```

Splintf formats according to a format specifier and returns the resulting string.

```
package main

import "fmt"

func main() {
    const name, age = "Kim", 22
    s := fmt.Sprintf("%s is %d years old.\n", name, age)
    fmt.Print(s)
}
```

Output:

```
Kim is 22 years old.
```
