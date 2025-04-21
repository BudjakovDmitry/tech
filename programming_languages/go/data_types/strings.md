# Strings

## String Literals

To create string value use __double quotes__: `"Hello world"` or __back quites__ (or
back ticks): `` ` ``. It is not allowed to use single quotes to create strings in
Go.

```
var name string = "Sam"
planet := `Earth`
```

Using back quotes will create _raw_ string literal. In a raw string literal, any
character may appear between quotes, except of back quotes.

```
Say "hello" to Go!
```

Backslashes have no special meaning inside of raw string literals. For instance `\n`
will appear as the actual characters, backslash `\` and letter `n`. Unlike interpreted
string literals, in which `\n` would insert an actual new line.

Raw string literals may also be used to create multi-line strings:

```
`Go is
- expressive,
- concise,
- clean and
- efficient.
```

Interpreted string literals are character sequences between double quotes, as in
`"bar"`. Within the quotes, any character may apper except of newline and unescaped
double quotes.

```
"Say \"hello\" to Go!
```

## Formatting strings

```
package main

import "fmt"

func main() {
    value := 2
    fmt.Printf("The type of value is %T\n", value)
}
```

`%T` tells to print type of the variable rather than its value.
