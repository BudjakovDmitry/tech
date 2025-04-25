# ReadFile

```
func ReadFile(name string) ([]byte, error)
```

`ReadFile` reads the named file amd returns the contents. A successful cal returns
`err == nil`, not `err == EOF`. Because `ReadFile` reads the whole file, it does not
treat an EOF from Read as an error to be reported.

```
package main

import (
    "log"
    "os"
)

func main() {
    data, err := os.ReadFile("hello")
    if err != nil {
        log.Fatal(err)
    }
    os.Stdout.Write(data)
}
```
