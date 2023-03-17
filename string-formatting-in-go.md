# String Formatting in Go

```go
package main

import (
	"fmt"
)

func main() {
	// Basic Println
	fmt.Println("Test only")
	fmt.Println("Test", 123)
	fmt.Println("Test", 123, 0.23, true)
	// fmt.Println("Test" + 123)          // -> Error

	fmt.Printf("%v \n", 1)                // Print Formatter" dapat digunakan untuk memformat angkat, variabel dan string dalam satu string parameter.
	fmt.Printf("Saya %s dan umur saya %d tahun\n", "Andi", 12)
	fmt.Printf("Kebalikan dari %t adalah %t\n", true, false)
	fmt.Printf("%f\n", 0.25)              // 0.250000
	fmt.Printf("%2.4f\n", 0.254522452523) // 0.2545
	fmt.Printf("%4.2f\n", 0.254522452523) // 0.25
	fmt.Printf("%b\n", 12)                // 1100
	fmt.Printf("%b\n", 30)                // 111100
	fmt.Printf("%x\n", 12)                // c
	fmt.Printf("%x\n", 30)                // 1e
	fmt.Printf("%T\n", 20)                // int
	fmt.Printf("%T\n", 12.25)             // float
	fmt.Printf("%T\n", true)              // bool

	var p *int                            // declare as pointer
        var q int = 42
        p = &q                                // pointer to q
        fmt.Printf("%p", p)                   // 0x40e020 (prints the memory address)
}
```
