# Scan

```
func Scan(a ...any) (n int, err error)
```

Scan scans text read from standard input, storing successive space-separated values into
successive arguments. Newlines count as space. It returns the number of items
successfully scanned. If that is less than the number of arguments, err will report why.

```
package main

import "fmt"

func main() {
  var name string
  fmt.Print("Your name: ")
  fmt.Scan(&name)
  fmt.Println("Hello", name)
}
```
