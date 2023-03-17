# Blank Identifier

Gunakan (\_) untuk variabel yang tidak ingin digunakan

```go
package main

import (
    "errors"
    "fmt"
)

func Pembagian(a, b float64) (float64, error) {
    if b == 0 {
        return 0, errors.New("b should not 0")
    } else {
        return a/b, nil
    }
}

func main() {
    result, _:= Pembagian(12,0)
    fmt.Println(result)
}
```
