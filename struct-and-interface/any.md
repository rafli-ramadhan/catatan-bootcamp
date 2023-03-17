# Any

Any -> Interface untuk Go version >= 1.18&#x20;

```go
package main

import (
	"fmt"
)

func main() {
    var name any = "member_01"
    stringName := name.(string)
    fmt.Println(stringName)

    var number1 any = 2
    var number2 any = 3
    hasil := number1.(int64) + number2.(int64)
    fmt.Println(hasil)

    var user any = []string{"member_01", "member_02", "member_03"}
    arrayUser := user.([]string)
    for _, v := range arrayUser {
        fmt.Println(v)
    }
}
```



```go
package main

import "fmt"

func main() {
    type any interface{}
    var user any = []string{"member_01", "member_02", "member_03"}
    arr := user.([]string)
    switch result := user.(type) {
    case string:
        fmt.Printf("String", result)
    case int:
        fmt.Printf("Integer", result)
    case []string:
        for _, v := range arr { // cannot range over user (variable of type any)
            fmt.Print(v)
        }
    }
}
```



