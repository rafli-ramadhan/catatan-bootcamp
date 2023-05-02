# Data Type Conversion

## Contoh _code_ konversi integer ke float

Int di ubah menjadi float bisa, karena di tipe data float terdapat integer (contoh = 1, 2, 3, dsb).

```go
package main

import (
	"fmt"
)

func main() {
	var num1 int = 2
	var num2 float64 = float64(num1)
	fmt.Println(num2)
	fmt.Printf("%T\n", num2)
}
```

```
2
float64
```

## Contoh _code_ konversi float ke integer

Float di konversi menjadi Int tidak bisa, karena di tipe data integer tidak terdapat data desimal.

```go
package main

import (
	"fmt"
)

func main() {
	var num1 float64 = 2.0
	var num2 float64 = int(num1)
	fmt.Println(num2)
	fmt.Printf("%T", num2)
}
```

```
cannot use int(num1) (value of type int) as type float64 in variable declaration
```

## Contoh _code_ konversi boolean ke string

```go
package main

import (
	"fmt"
)

func main() {
	var isFalse bool = true
	fmt.Printf(string(isFalse))
}
```

```
cannot convert isFalse (variable of type bool) to type string
```

## Contoh _code_ konversi string menjadi rune dan byte

```go
package main
 
import (
    "fmt"
)
 
func main() {
    s := "GÖLANG PROGRAMMING golang programming" // Ö is a non-ASCII character 
 
    s_rune := []rune(s)
    s_byte := []byte(s)
     
    fmt.Println(s_rune)
    fmt.Println(s_byte)
}
```

```
[71 214 76 65 78 71 32 80 82 79 71 82 65 77 77 73 78 71 32 103 111 108 97 110 103 32 112 114 111 103 114 97 109 109 105 110 103]
[71 195 150 76 65 78 71 32 80 82 79 71 82 65 77 77 73 78 71 32 103 111 108 97 110 103 32 112 114 111 103 114 97 109 109 105 110 103]
```

Reference :

[https://golangdocs.com/rune-in-golang](https://golangdocs.com/rune-in-golang)
