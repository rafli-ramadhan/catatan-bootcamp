# Float

Default value dari tipe data float adalah 0.

<figure><img src="../.gitbook/assets/float and complex.png" alt=""><figcaption></figcaption></figure>

## Contoh _code_

```go
package main

import "fmt"

var num float64

func main() {
    if num == 0 {
        fmt.Println("zero value")
    }
    num = 1.2
    fmt.Println(num)
}
```

```
zero value
1.2
```
