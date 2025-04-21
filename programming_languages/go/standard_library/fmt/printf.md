# Printf

```
func Printf(format string, a ...any) (n int, err error)
```

Printf formats according to a format specifier and writes to standard output. It
returns the number if bytes written and any write error encountered.

```
package main

import "fmt"

func main() {
    const name, age = "Kim", 22
    fmt.Printf("%s is %d years old.\n", name, age)
    
    // It is conventional not to worry about any error returned by Printf.
}
```

Output:

```
Kim is 22 years old.
```
