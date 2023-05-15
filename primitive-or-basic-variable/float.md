# Float

Tipe data numerik desimal di Golang bisa disimpan dalam tipe data float. Default value dari tipe data float adalah 0. Sementara untuk tipe desimal dengan bilangan imaginer dapat disimpan dengan tipe data complex.

<figure><img src="../.gitbook/assets/float and complex.png" alt=""><figcaption></figcaption></figure>

## Contoh _code_ 1

```go
package main

import "fmt"

var num1 float64
var num2 complex64

func main() {
    if num1 == 0 {
        fmt.Println(num1)
    }
    num1 = 1.2
    fmt.Println(num1)
    
    if num2 == 0 {
        fmt.Println(num2)
    }
    num2 = 1.2 + 1i
    fmt.Println(num2)
}
```

```
0
1.2
(0+0i)
(1.2+1i)
```

## Contoh _code_ 2

```go
package main

import "fmt"

var num1 complex64 = 2 + 2i
var num2 complex64 = complex(1, 2)

func main() {
    fmt.Println(num1)
    fmt.Println(num2)
    // untuk mendapatkan bagian real dan imaginer
    fmt.Println(real(num1))
    fmt.Println(imag(num1))
}
```

```
(2+2i)
(1+2i)
2
2
```
