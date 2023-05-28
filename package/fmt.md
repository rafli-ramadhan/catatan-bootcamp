# Fmt

fmt.Println -> bisa untuk print tipe data int, float, bool, string, arr, map, slice dan struct.

fmt.Printf -> hanya untuk print formatting string

fmt.Sprintf -> untuk membuat variabel string dengan variabel dinamis

fmt.FPrintf atau fmt.Fprintln -> untuk menampilkan value ke sisi client

fmt.Scanln -> untuk memperoleh input dari sisi server -> tapi input tidak boleh dipisahkan oleh spasi.

## Contoh _code_ penggunaan print

```go
package main

import "fmt"

func main() {
	fmt.Print("Hello")
	fmt.Print("for integer        :", 123)
	fmt.Print("for scientific notation :", 3 + 5i)
	fmt.Print("for float          :", 1.234)
	fmt.Print("float rounding     :", 12.3456)
	fmt.Print("string example     :", "member 01")
	fmt.Print("boolean example    :", false)
	var someInterface interface{} = 123
	fmt.Print("for pointer    	:", &someInterface)
	fmt.Print("some interface     :", someInterface)
	fmt.Print("some array         :", [3]int{1,2,3})
	fmt.Print("some slice         :", []int{1,2,3})
	fmt.Print("some map           :", map[string]interface{}{
		"username": "member_01",
		"password": "Test123",
	})
	// struct
	type User struct {
		Username string
		Password string
	}
	user := User{"member_01", "Test123"}
	fmt.Print("some struct        :", user)
	// channel
	var ch = make(chan int)
	go func() {
		ch<-1
	}()
	fmt.Print("some channel       :", <-ch)
	// function
	someFunc := func (a, b int) int {
		return a + b
	}
	fmt.Print("some func          :", someFunc(2, 3))
}
```

```
Hellofor integer        :123for scientific notation :(3+5i)for float          :1.234float rounding     :12.3456string example     :member 01boolean example    :falsefor pointer  
        :0xc000040260some interface     :123some array         :[1 2 3]some slice         :[1 2 3]some map           :map[password:Test123 username:member_01]some struct        :{member_01 Test123}some channel       :1some func          :5
```

## Contoh _code_ penggunaan println

```go
package main

import "fmt"

func main() {					
	fmt.Println("Hello")
	fmt.Println("for integer        :", 123)
	fmt.Println("for scientific notation :", 3 + 5i)
	fmt.Println("for float          :", 1.234)
	fmt.Println("float rounding     :", 12.3456)
	fmt.Println("string example     :", "member 01")
	fmt.Println("boolean example    :", false)
	var someInterface interface{} = 123
	fmt.Println("for pointer    	:", &someInterface)
	fmt.Println("some interface     :", someInterface)
	fmt.Println("some array         :", [3]int{1,2,3})
	fmt.Println("some slice         :", []int{1,2,3})
	fmt.Println("some map           :", map[string]interface{}{
		"username": "member_01",
		"password": "Test123",
	})
	// struct
	type User struct {
		Username string
		Password string
	}
	user := User{"member_01", "Test123"}
	fmt.Println("some struct        :", user)
	// channel
	var ch = make(chan int)
	go func() {
		ch<-1
	}()
	fmt.Println("some channel       :", <-ch)
	// function
	someFunc := func (a, b int) int {
		return a + b
	}
	fmt.Println("some func          :", someFunc(2, 3))
}
```

```
Hello
for integer        : 123
for scientific notation : (3+5i)
for float          : 1.234
float rounding     : 12.3456
string example     : member 01
boolean example    : false
for pointer     : 0xc000040260
some interface     : 123
some array         : [1 2 3]
some slice         : [1 2 3]
some map           : map[password:Test123 username:member_01]
some struct        : {member_01 Test123}
some channel       :  1
some func          :  5
```

## Contoh _code_ penggunaan printf

```go
package main

import (
	"fmt"
)

func main() {
	fmt.Printf("for binary value   : %b \n", 10)
	fmt.Printf("for integer        : %d\n", 123)
	fmt.Printf("for scientific notation : %e \n", 3 + 5i)
	fmt.Printf("for float          : %f \n", 1.234)
	fmt.Printf("float rounding     : %.2f\n", 12.3456)
	fmt.Printf("string example     : %s\n", "member 01")
	var someInterface interface{} = 123
	fmt.Printf("type data of %s is : %T\n", "member_01", "member_01")
	fmt.Printf("type data of %d is : %T\n", someInterface, someInterface)
	fmt.Printf("for pointer    	   : %p\n", &someInterface)
	fmt.Printf("some interface     : %v\n", someInterface)
	fmt.Printf("some array         : %v\n", [3]int{1,2,3})
	fmt.Printf("some slice         : %v\n", []int{1,2,3})
	// struct
	type User struct {
		Username string
		Password string
	}
	user := User{"member_01", "Test123"}
	fmt.Printf("some struct        : %+v\n", user)
	// channel
	var ch = make(chan int)
	go func() {
		ch<-1
	}()
	fmt.Printf("some channel       : %v\n", <-ch)
	fmt.Printf("for boolean        : %t\n", false)
	// switch index
	fmt.Printf("switch index       : %[2]d %[1]d\n", 11, 22)
	fmt.Printf("switch index       : %[3]s %[2]d %[1]d\n", 11, 22, "some_string")
	fmt.Printf("switch index       : %[4]t %[3]s %[2]d %[1]d\n", 11, 22, "some_string", true)
}
```

```
for binary value   : 1010 
for integer        : 123
for scientific notation : (3.000000e+00+5.000000e+00i)
for float          : 1.234000
float rounding     : 12.35
string example     : member 01
type data of member_01 is : string
type data of 123 is : int
for pointer        : 0xc000040260
some interface     : 123
some array         : [1 2 3]
some slice         : [1 2 3]
some struct        : {Username:member_01 Password:Test123}
some channel       : 1
for boolean        : false
switch index       : 22 11
switch index       : some_string 22 11
switch index       : true some_string 22 11
```

## Printf vs Sprintf

```go
package main
  
import (
    "error"
    "fmt"
)

func main() {
    // a := fmt.Printf("Test %d", 123) // ssignment mismatch: 1 variable but fmt.Printf returns 2 values

    b := fmt.Sprintf("Test %d", 123)
    fmt.Println(b)
    
    err = errors.New("test error")
    if err != nil {
        log.Print(fmt.Sprintf("error : %s", err))
    }
}
```
