# Boolean

Default value dari tipe data boolean adalah False.

## Contoh _code_

```go
package main

import "fmt"

var IsTrue bool

func main() {
    fmt.Println(IsTrue)
    fmt.Println(!IsTrue)
    if IsTrue {             // -> if IsTrue == true
        fmt.Println(true)
    }
    if !IsTrue {            // -> if IsTrue == false
        fmt.Println(false)
    }
}
```

```
false
true
false
```
