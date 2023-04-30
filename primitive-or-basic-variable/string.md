# String

Default value dari tipe data string adalah string kosong atau "".

## Contoh _code_

```go
package main

import "fmt"

var str string

func main() {
    if str == "" {
        fmt.Println("it is an empty string")
    }
    str = "test"
    fmt.Println(str)
}
```

```
it is an empty string
test
```
