# Var vs Operator :=

## **Var**

Keunggulan deklarasi variabel dengan var adalah bisa di inisiasi di luar function dan bisa digunakan di level package. Kekurangannya tidak bisa untuk handle function yang return multi variabel.

## Operator :=

Keunggulan deklarasi variabel dengan operator := adalah bisa untuk menampung value yang belum diketahui tipe datanya dan bisa untuk menampung return multi variabel dari suatu _function_. Kekurangannya tidak bisa dideklarasikan di luar function.

## Contoh _code_

```go
package main

import "fmt"

var num1 int = 2
// num2 := 2 -> error non-declaration statement outside function body

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
