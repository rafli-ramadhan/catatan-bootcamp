# Pointer (Pass By Reference)

Kelebihan pointer -> memungkinkan penggunaan memory address seminimal mungkin -> suatu variabel bisa di inisiasi dengan value variabel lain, tanpa membuat memory address baru -> disebut reference -> variabel 1 dan variabel 2 punya value yang sama dan memory address yang sama.

Kekurangan pointer -> jika nilai variabel yang me-reference variabel lain diubah, variabel lain tersebut juga akan berubah.

```go
package main
import "fmt"

func main() {
  var num  int
  var ptr *int
    
  num = 22
  fmt.Println("Address of num:",&num)
  fmt.Println("Value of num:",num)

  // assign the memory address of variable to the pointer
  ptr = &num
  fmt.Println("\nAddress of pointer:",ptr)
  fmt.Println("Value of pointer:",*ptr)
    
  num = 11
  fmt.Println("\nAddress of pointer:",ptr)
  fmt.Println("Value of pointer:",*ptr)
    
  *ptr = 2
  fmt.Println("\nAddress of num:",&num)
  fmt.Println("Value of num:",num)
}
```

```
Address of num: 0xc0000ba000
Value of num: 22

Address of pointer: 0xc0000ba000
Value of pointer: 22

Address of pointer: 0xc0000ba000
Value of pointer: 11

Address of num: 0xc0000ba000
Value of num: 2
```

## Pointer dengan Struct

```go
package main

import "fmt"

func main() {
	type User struct {
		Name string
		Age  int
	}
	var userA = User{
		Name: "member_01",
		Age:  21,
	}
	var data = &userA
	*data = User{"member_02", 22}
	fmt.Println(userA)
}
```

```
{member_02 22}
```

## Pointer dengan Map

```go
package main

import "fmt"

func main() {
	var someMap = map[string]int{
		"test1": 1,
		"test2": 2,
	}
	var data = &someMap
	fmt.Println(*data)
	*data = map[string]int{
		"test": 2,
	}
	fmt.Println(someMap)
}	
```

```
map[test1:1 test2:2]
map[test:2]
```
