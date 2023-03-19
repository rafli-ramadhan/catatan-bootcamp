# Struct, Embedded Struct, Struct Method

Struct bisa digunakan sebagai parameter untuk sebuah function

Function dalam struct -> Method

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

// embedded struct
type Address struct {
    City     string
    Province string
    Country  string
}

// embedded struct
type WorkAddress struct {
    City     string
    Province string
    Country  string
}

// struct method
func (user User) Greeting() {
    fmt.Printf("\nHi %s", user.name)
}

func main() {
    // struct declaration dengan struct literals
    var user1 User                                  // -> {  0 {  }}, zero value
    user1.name = "member_001"
    user1.email = "test01@gmail.com"
    user1.password = 1234
    user1.Address.City = "Jakarta"
    user1.WorkAddress.City = "Malang"

    var user2 User = User{}                         // -> {  0 {  }}, zero value
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
