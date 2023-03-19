# Interface

\-> Kumpulan definisi method (hanya definisi saja) dengan nama tertentu\
\-> Interface syaratnya harus method\
\-> Method sayaratnya harus struct

```go
package main

import "fmt"

type CustomerInterface interface {
	Greeting() string
}

type Account struct {
    Name string
}

type Customer struct {
	Name string
}

func (a Account) Greeting() string{
    return "Hi " + a.Name
}

func (c Customer) Greeting() string {
	return "Welcome " + c.Name
}

// satu function yang menampung beberapa struc dengan method sama.
func justCheck(customerInterface CustomerInterface) string {
    return customerInterface.Greeting()
}

func main() {
	customer1 := Customer{
		Name: "Firman",
	}
	fmt.Println(customer1.Greeting())
    fmt.Println("Bot : " + justCheck(customer1))

	account1 := Account{
		Name: "Andi",
	}
	fmt.Println(account1.Greeting())
    fmt.Println("Bot : " + justCheck(account1))
}
```

```
Welcome Firman
Bot : Welcome Firman
Hi Andi
Bot : Hi Andi
```

```go
package main

import (
	"fmt"
)

func main() {
    var name any = "member_01"
    stringName := name.(string)
    fmt.Println(stringName)

    var number1 any = 2
    var number2 any = 3
    hasil := number1.(int) + number2.(int)
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
