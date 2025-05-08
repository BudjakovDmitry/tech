# ParseFloat

```
func ParseFloat(s string, bitSize int) (float64, error)
```

`ParseFloat` converts the string `s` to a floating-point number with the precision
specified by `bitSize`: 32 for `float32`, or 64 for `float64`. When `bitSize == 32`,
the result still has type `float64`, but it will be convertable to `float32` without
changing its value.

