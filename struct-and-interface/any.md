# Interface Kosong atau Any

Interface kosong dapat di inisiasi menggunakan `any` untuk Go version di atas 1.18. Untuk memperoleh nilai dari interface kosong dapat menggunakan _type assertion_ seperti contoh _code_ berikut.

```go
package main

import "fmt"

func main() {
    var test any = "test"
    // type assertion
	str, ok := test.(string)
	fmt.Println(ok)
	fmt.Println(str)
}
```

```
true
test
```

```go
package main
import "fmt"

func main() {
	var test any = func(a, b int) int {
		return a+b
	} 
	// type assertion
	someFunc, ok := test.(func(a, b int) int)
	fmt.Println(ok)
	fmt.Println(someFunc(2,3))
}
```

```
true
5
```

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	ch := make(chan int)
	// type assertion
	go func() {
		var result interface{} =<- ch
		fmt.Println(result)
	}()
	ch<-1
	time.Sleep(1 * time.Second)
}
```

```
1
```

```go
package main

import (
	"fmt"
)

func main() {
    // type assertion
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

```
member_01
5
member_01
member_02
member_03
```

```go
package main

import (
	"fmt"
)

func main() {
	var errors any = fmt.Errorf("some error")
	res := errors.(error)
	fmt.Println(res)

	// this code will give an panic
	var errors2 any = nil
	res2 := errors2.(error)
	fmt.Println(res2)
}
```

```
panic: interface conversion: interface is nil, not error

goroutine 1 [running]:
main.main()
	/tmp/sandbox3945396184/prog.go:13 +0x99
Program exited.
```

## Type Switch

Type switch digunakan untuk memperoleh tipe data dari suatu nilai dalam interface kosong. Type switch memiliki format seperti di bawah ini. Banyaknya case dapat disesuaikan sesuai kebutuhan.

```go
switch v := i.(type) {
case int:
    // program
case string:
    // program
case float64:
    // program
case bool:
    // program
case []string:
    // program
default:
    // program
}
```

Contoh _code_ seperti di bawah ini.

```go
package main

import "fmt"

func main() {
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

```
member_01
member_02
member_03
```

Reference : [https://go.dev/tour/methods/16#:\~:text=%EE%80%80Type%EE%80%81%20%EE%80%80switches%EE%80%81.%20A%20%EE%80%80type%20switch%EE%80%81%20is%20a%20construct,the%20value%20held%20by%20the%20given%20interface%20value.](https://go.dev/tour/methods/16)
