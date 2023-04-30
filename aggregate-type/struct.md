# Struct

Struct merupakan tipe data aggregate dalam Golang yang dapat dideklarasikan sebagai berikut :

```go
type User struct{
	name      string
	age       int
    	isMarried bool
}
```

## Default Value

Default value dari suatu struct akan mengikuti default value dari tipe data setiap parameternya.

```go
package main

import (
	"fmt"
)

func main() {
	type User struct{
		name      string
		age       int
		isMarried bool
	}

	var user User = User{}
	fmt.Println(user)
}
```

```
{ 0 false}
```

## Embedded Struct

Struct yang dideklarasikan dalam suatu struct. Contohnya untuk struct User di bawah ini terdapat parameter Address dan WorkAddress yang juga merupakan struct.

```go
type User struct {
    name     string
    email    string
    password int
    Address
    WorkAddress
}

type Address struct {
    City     string
    Province string
    Country  string
}

type WorkAddress struct {
    City     string
    Province string
    Country  string
}
```

## Struct & Method

Method merujuk pada suatu function yang dimiliki oleh suatu struct. Contohnya struct User di bawah ini memiliki method Greeting() yang merupakan function milik struct User.

```go
type User struct {
    name     string
    email    string
    password int
    Address
    WorkAddress
}

func (user User) Greeting() {
    fmt.Printf("\nHi %s", user.name)
}
```

## Contoh _code_

Berikut adalah contoh _code_ implementasi dari embedded struct dan method.

```go
package main

import (
	"fmt"
)

type User struct {
    name     string
    email    string
    password int
    Address
    WorkAddress
}

type Address struct {
    City     string
    Province string
    Country  string
}

type WorkAddress struct {
    City     string
    Province string
    Country  string
}

func (user User) Greeting() {
    fmt.Printf("\nHi %s", user.name)
}

func main() {
    var user1 User
    user1.name = "member_001"
    user1.email = "test01@gmail.com"
    user1.password = 1234
    user1.Address.City = "Jakarta"
    user1.WorkAddress.City = "Malang"

    var user2 User = User{}
    var address2 Address = Address{}
    var workaddress2 WorkAddress = WorkAddress{}
    address2 = Address{"Semarang", "Jawa tengah", "Indonesia"}
    workaddress2 = WorkAddress{"Jakarta", "DKI Jakarta", "Indonesia"}
    user2 = User{"member_002", "test02@gmail.com", 1234, address2, workaddress2}

    var user3 User = User{
        name: "member_003",
        Address: Address{
            City: "Solo",
        },
        WorkAddress: WorkAddress{
            City: "Jakarta",
        },
    }

    user := []User{user1, user2, user3}
    for i, v := range user {
        fmt.Printf("User %d : %v\n", i+1, v)
    }

    user1.Greeting()
    user2.Greeting()
    user3.Greeting()
}
```

```
User 1 : {member_001 test01@gmail.com 1234 {Jakarta  } {Malang  }}
User 2 : {member_002 test02@gmail.com 1234 {Semarang Jawa tengah Indonesia} {Jakarta DKI Jakarta Indonesia}}
User 3 : {member_003  0 {Solo  } {Jakarta  }}

Hi member_001
Hi member_002
Hi member_003
```

## Komparasi Struct

Membandingkan apakah struct 1 dan struct 2 memiliki value yang sama atau berbeda.

```go
package main

import (
	"fmt"
)

func main() {
	type User struct{
		name string
		age  int
	}

	var user User = User{}
	fmt.Println(user)
	var user2 User = User{}
	if user == user2 {
		fmt.Printf("true")
	}
}
```

```
{ 0}
true
```

