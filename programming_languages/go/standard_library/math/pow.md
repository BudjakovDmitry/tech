# func Pow

```
func Pow(x, y float64) float64
```

Pow returns x**y.

```
package main

import (
    "fmt"
    "math"
)

func main() {
    c := math.Pow(2, 3)
    fmt.Printf("%.1f", c)
}
```
