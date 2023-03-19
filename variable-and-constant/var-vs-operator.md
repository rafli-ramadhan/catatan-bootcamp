# Var vs Operator :=

Keunggulan deklarasi variabel dengan var -> bisa di inisiasi di luar function, bisa digunakan di level package. Kekurangan -> tidak bisa untuk handle function yang return multi variabel.\
Keunggulan operator := -> Bisa untuk menampung value yang belum diketahui tipe datanya dan bisa untuk menampung return multi variabel dari suatu function. Kekurangan -> tidak bisa dideklarasikan di luar function.

```go
package main

import "fmt"

var num1 int = 2
// num2 := 2 // non-declaration statement outside function body

func main() {
    num2 := 2
    fmt.Println(num1)
    fmt.Println(num2)
}
```

```
2
2
```
