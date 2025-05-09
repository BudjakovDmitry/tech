# Go data types

## Numbers

* [Integers](integers.md)
* [Floats](floats.md)
* [Complex](complex.md)

### Operations with numbers

*  `+` addition;
* `*` multiply;
* `/` division;
* `==` equal to;
* `!=` not equals to;
* `<` smaller than;
* `>` greater than;
* `<=` smaller or equal;
* `>=` greater or equal;
* `+=` (`a = a + b` is the same as `a += b`);
* `-=` (`a = a - b` is the same as `a -= b`);
* `++` (`i++` is the same as `i = i + 1`);

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

### to float

If we want to add floating point number and integer, we need convert `int` to `float`:

```
var amount = 1000
var rate = 5.5

// invalid operation: mismatched types int and float
var value = amount * (1 + rate / 100)

// converting int to float64
var value = float64(amount) * (1 + rate / 100)
```

### to string

Use `string` function to convert to string.

```
data, _ := os.ReadFile("hello")  // ReadFile returns []byte
dataText := string(data)
```
