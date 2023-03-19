# Variable vs Constant

Variabel -> nilai bisa diubah-ubah meskipun sudah di inisiasi suatu value.\
Const -> nilai tidak bisa diubah saat sudah di inisiasi suatu value.

```go
package main

import "fmt"

func main() {
    var num1 int = 2
    fmt.Println(num1)
    num1 = 3
    fmt.Println(num1)
    
    const num2 int = 2
    fmt.Println(num2)
    // num2 = 3           // cannot assign to num2 (constant 2 of type int)
}
```

```
2
3
2
```
