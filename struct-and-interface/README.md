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

Semisal ada go module bernama "go-rest-api". Didalamnya terdapat 2 file yaitu repo.go dan handler.go. Di dalam file repository.go dirinci pada _code_ di bawah ini. Pada file tersebut juga terdapat interface yaitu Repositorier.

```go
package repository

type repo struct {}

func NewRepository() *repo {
	return &repo{}
}

type Repositorier interface {
	CheckUserByName(username string) (isExist bool, err error) {}
	Create(username string, password string) (err error) {}
}

func (r *random) CheckUserByName(username string) (isExist bool, err error) {}

func (r *random) Create(username string, password string) (err error) {}
```

Di file yang berbeda semisal handler.go membutuhkan method GetNameById dan Create dari package repository.

```go
package handler

import (
	"go-rest-api/repository"
)

type handler struct {
	repo repository.Repositorier
}

func NewHandler(repo repository.Repositorier) *handler {
	return &handler{
		repo: repo,
	}
}

func (h *handler) Example(username, password string) (err error) {
	exist := r.repo.CheckUserByName(id)
	// lanjutan code
	err := r.repo.Create(username, password)
	// lanjutan code
}
```

Semisal ingin membuat unit test dari handler seperti _code_ dibawah ini. Repository yang di inputkan pada NewHandler perlu dibuat mocking nya, karena unit testing hanya berfungsi untuk test 1 package saja.

```go
package product

import (
	"testing"
	"sales-go/mocks/repository"
)

func TestExample(t *testing.T) {
	repoMock :=
	handler := NewHandler(repoMock)
	err := handler.Example("member_01", "Test123")
	// lanjutan code
}
```

```go
package random

import (
	"github.com/stretchr/testify/mock"
)

type RepoMock struct {
	mock.Mock
}

func NewRandom() *RepoMock {
	return &RepoMock {}
}


func (r *random) CheckUserByName(username string) (isExist bool, err error) {}
func (r *random) Create(username string, password string) (err error) {}
```

Referensi:

{% embed url="https://stackoverflow.com/questions/39092925/why-are-interfaces-needed-in-golang" %}
