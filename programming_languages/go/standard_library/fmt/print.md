# Print

```
func Print(a ...any) (n int, err error)
```

Print formats using the default formats for its operands and writes to standard output.
Spaces are added between operands when neither is a string. It returns the number of
bytes written and any write error encountered.

```
package main

import "fmt"

func main() {
    const name, age = "Kim", 22
    fmt.Print(name, " is ", age, " years old.\n")
    
    // It is conventional not to worry about any error returned by Print
}
```

Output:

```
Kim is 22 years old.
```
