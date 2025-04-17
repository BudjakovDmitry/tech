# Go data types

## Numbers

* [Integers](integers.md)
* [Floats](floats.md)
* [Complex](complex.md)

## Strings

* [strings](strings.md)

## Booleans

* [booleans](boolean.md)

## Converting

If we want to add floating point number and integer, we need convert `int` to `float`:

```
var amount = 1000
var rate = 5.5

// invalid operation: mismatched types int and float
var value = amount * (1 + rate / 100)

// converting int to float64
var value = float64(amount) * (1 + rate / 100)
```
