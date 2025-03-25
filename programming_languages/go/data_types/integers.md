# Integers

## Unsigned integers (no negatives)

* uint8 the set of all unsigned 8-bit integers (0 to 255)
* byte - an alias for unit8
* uint16 the set of all unsigned 16-bit integers (0 to 65535)
* uint32 the set of all unsigned 32-bit integers (0 to 4294967295)
* uint64 the set of all unsigned 64-bit integers (0 to 18446744073709551615)

```
var number uint8 = 128
```

## Signed integers

int8 the set of all signed  8-bit integers (-128 to 127)
int16 the set of all signed 16-bit integers (-32768 to 32767)
int32 the set of all signed 32-bit integers (-2147483648 to 2147483647)
rune - an alias for int32. Represents a Unicode code point
int64 the set of all signed 64-bit integers (-9223372036854775808 to 9223372036854775807)

## Machine dependent types

When you use this type, your computer will automatically figure out how big these are
supposed to be.

* uint (32 or 64 bits) If operating system is 32 or 64-bit it will use 32 or 64 bits to
represent an unsigned integer.
* int (same as uint)
* uintptr
