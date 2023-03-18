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

