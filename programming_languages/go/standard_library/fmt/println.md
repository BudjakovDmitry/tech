# Println

```
func Println(a ...any) (n int, err error)
```

Println formats using the default formats for its operands and writes to standard
output. Spaces are always added between operands and a newline is appended. It returns a
number of bytes written and any write error encountered.

```
package main

import "fmt"

func main() {
  const name, age = "Kim", 22
  fmt.Println(name, "is", age, "years old.")
  
  // It is conventional not to worry about any error returned by Println.
}
```

Output:

```
Kim is 22 years old.
```
