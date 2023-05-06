# Interface

Interface merupakan suatu tipe data yang berisi kumpulan definisi method (hanya definisi saja) dengan nama tertentu. Untuk default value dari interface adalah nil. Interface syaratnya harus method dan method syaratnya harus ada kepemilikan. Contoh untuk 2 method Greeting _code_ di bawah ini merupakan method milik struct Account dan Customer. Method tersebut dapat ditampung dalam sebuah interface bernama CustomerInterface.

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

// function untuk menggunakan interface dari method beberapa struct.
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



```go
package main

import(
	"fmt"
)

// type declaration
type Value string

func (v Value) Hello() {
	fmt.Println("Hello", v)
}

type Example interface {
	Hello()
}

func main() {
	var string1 Value = "Andi"
	string1.Hello()
	var interface1 Example = string1
	interface1.Hello()

	var string2 Value = "Utsman"
	string2.Hello()
	var interface2 Example = string2
	interface2.Hello()
}
```

```
Hello Andi
Hello Andi
Hello Utsman
Hello Utsman
```

## Kegunaan Interface



[https://stackoverflow.com/questions/39092925/why-are-interfaces-needed-in-golang](https://stackoverflow.com/questions/39092925/why-are-interfaces-needed-in-golang)
