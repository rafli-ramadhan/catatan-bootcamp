# Tricky Case

Kenapa saat akses data variabel pointer di struct tidak pakai \*, sementara di variabel primitif pakai \*.

```go
package main

import "fmt"

func main() {
  // case print value primitive variable
  var num1 int = 2
  var num2 *int
  num2 = & num1
  fmt.Println(num2)  // -> print memory address
  fmt.Println(*num2) // -> print value
 
  // case print value aggregate variable
  type Person struct {
    name string
    age int
  }
  person1 := Person{"Andi", 25}
  var person2 *Person
  person2 = &person1

  fmt.Println("Name:", person2.name) // -> print value
  // fmt.Println("Name:", *ptr.name) -> invalid operation
  fmt.Println("Age:", person2.age)   // -> print value
}
```

```
0xc00001a038
2
Name: Andi
Age: 25
```
