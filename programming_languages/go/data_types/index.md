# Go data types

## Numbers

* [Integers](integers.md)
* [Floats](floats.md)
* [Complex](complex.md)

## Strings

* [strings](strings.md)

## Booleans

* [booleans](boolean.md)

## Null values

All Go value types come with a so-called "null value" which is the value stored in a
variable if no other value is explicitly set.

Here is a list of the null values for the different types:

* `int` -> `0`
* `float64` -> `0.0`
* `string` -> `""` (i.e., an empty string)
* `bool` -> `false`

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
