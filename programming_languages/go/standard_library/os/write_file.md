# WriteFile

```
func WriteFile(name string, data []byte, perm FileMode) error
```

`WriteFile` writes data to the named file, creating it if necessary. If the file does
not exist, `WriteFile` creates it with permissions `perm` (before umask); otherwise
`WriteFile` truncates it before writing, without changing permissions. Since `WriteFile`
requires multiple system calls to complete, a failure mid-operation can leave the file
in a partially written state.

```
package main

import (
    "log"
    "os"
)

func main() {
    err := os.WriteFile("hello", []byte("Hello, Gophers!"), 0666)
    if err != nil {
        log.Fatal(err)
    }
}
```