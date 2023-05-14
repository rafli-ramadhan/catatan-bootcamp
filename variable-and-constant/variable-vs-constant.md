# Variable vs Constant

Variabel dan constant di golang sama-sama dapat di inisiasi suatu value dengan tipe data tertentu. Bedanya, nilai dari suatu constant tidak bisa diubah saat sudah di inisiasi suatu value.

## Contoh _code_

```go
package main

import "fmt"

func main() {
    var num1 int = 2
    fmt.Println(num1)

    // num1 di inisiasi dengan value berbeda
    num1 = 3
    fmt.Println(num1)
    
    const num2 int = 2
    fmt.Println(num2)

    // num2 di inisiasi dengan velue berbeda akan memunculkan error :
    // cannot assign to num2 (constant 2 of type int)
}
```

```
2
3
2
```

## Contoh _code_ Deklarasi Multi Variabel dan Constant

Contoh _code_ untuk deklarasi multi variabel dan constant dapat dilihat di bawah ini.

```go
package main

import "fmt"

var (
	num1 = 1
	num2 = 2
	num3 = 3
)

func main() {
	var (
		num4 = 1
		num5 = 2
		num6 = 3
	)
	num7, num8, num9 := 1,2,3

    fmt.Println(num1)
    fmt.Println(num2)
    fmt.Println(num3)
    fmt.Println(num4)
    fmt.Println(num5)
    fmt.Println(num6)
    fmt.Println(num7)
    fmt.Println(num8)
    fmt.Println(num9)
}
```

```go
package main

import "fmt"

const (
	num1 = 1
	num2 = 2
	num3 = 3
)

func main() {
	const (
		num4 = 1
		num5 = 2
		num6 = 3
	)

    fmt.Println(num1)
    fmt.Println(num2)
    fmt.Println(num3)
    fmt.Println(num4)
    fmt.Println(num5)
    fmt.Println(num6)
}
```
