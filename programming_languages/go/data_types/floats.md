# Floats

* float32 (IEEE-754 32-bit floating-point numbers);
* float64 (IEEE-754 64-bit floating-point numbers).

## Literals

A floating-point literal is a decimal or hexadecimal representation of a floating-point
constant.

```
float_lit = decimal_float_lit | hex_float_lit
```

A decimal floating-point literal consists of an integer part (decimal digits), a
decimal point, a fractional part (decimal digits), and an exponent part (e or E followed
by an optional sign and decimal digits). One of the integer part or the fractional part
may be elided; one of the decimal point or the exponent part may be elided. An exponent
value `exp` scales the mantissa (integer and fractional part) by 10<sup>exp</sup>.

```
decimal_float_lit = decimal_digits "." [ decimal_digits ] [ decimal_exponent ] |
                    decimal_digits decimal_exponent |
                    "." decimal_digits [ decimal_exponent ] .

decimal_exponent  = ( "e" | "E" ) [ "+" | "-" ] decimal_digits .
```

```
0.
72.40
072.40       // == 72.40
2.71828
1.e+0
6.67428e-11
1E6
.25
.12345E+5
1_5.         // == 15.0
0.15e+0_2    // == 15.0
```

A hexadecimal floating-point literal consists of a `0x` or `0X` prefix, an integer part
(hexadecimal digits), a radix point, a fractional part (hexadecimal digits), and an
exponent part (`p` or `P` followed by an optional sign and decimal digits). One of the
integer part or the fractional part may be elided; the radix point may be elided as
well, but the exponent part is required. (This syntax matches the one given in
IEEE 754-2008 §5.12.3.) An exponent value `exp` scales the mantissa (integer and
fractional part) by 2<sup>exp</sup>

```
hex_float_lit     = "0" ( "x" | "X" ) hex_mantissa hex_exponent .

hex_mantissa      = [ "_" ] hex_digits "." [ hex_digits ] |
                    [ "_" ] hex_digits |
                    "." hex_digits .

hex_exponent      = ( "p" | "P" ) [ "+" | "-" ] decimal_digits .
```

```
0x1p-2       // == 0.25
0x2.p10      // == 2048.0
0x1.Fp+0     // == 1.9375
0X.8p-0      // == 0.5
0X_1FFFP-16  // == 0.1249847412109375
0x15e-2      // == 0x15e - 2 (integer subtraction)
```

```
0x.p1        // invalid: mantissa has no digits
1p-2         // invalid: p exponent requires hexadecimal mantissa
0x1.5e-2     // invalid: hexadecimal mantissa requires p exponent
1_.5         // invalid: _ must separate successive digits
1._5         // invalid: _ must separate successive digits
1.5_e1       // invalid: _ must separate successive digits
1.5e_1       // invalid: _ must separate successive digits
1.5e1_       // invalid: _ must separate successive digits
```

## Converting to float

```
temperatureInt := 26
temperatureFloat := float64(temperatureInt)
```
