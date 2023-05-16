# Int & Uint (Unsigned Integer)

Default value dari tipe data integer adalah 0. Untuk Int8, Int16, Int32, Int64 perbedaannya terletak pada jumlah nilai minimal dan maksimal yang bisa ditampung. Selain itu, angka 8, 16, 32 dan 64 bisa disesuaikan dengan jumlah bit pada komputer yang digunakan.

<figure><img src="../.gitbook/assets/int.png" alt=""><figcaption></figcaption></figure>

Adapula uint (unsigned integer) yang digunakan untuk menampung value berupa integer positif.

<figure><img src="../.gitbook/assets/uint.png" alt=""><figcaption></figcaption></figure>

```go
package main

import "fmt"

var num int

func main() {
    if num == 0 {
        fmt.Println("zero value")
    }
    num = -5
    fmt.Println(num)
    
    num2 := uint(num)
    fmt.Println(num2)
}
```

```
zero value
-5
18446744073709551611
```
