# Int -> Float, Float -> Int

Int -> float -> Bisa, karena di tipe data float terdapat integer.\
Float -> Int -> Tidak bisa, karena di tipe data integer tidak terdapat float.

```go
package main

import (
	"fmt"
)

func main() {
	// int -> float64
	var a int = 2
	var b float64
	b = float64(a)
	fmt.Println(b)
	fmt.Printf("%T\n", b)

	// float64 -> int
	/*
	var c int
	c = int(2.5) // cannot convert 2.5 (untyped float constant) to int
	fmt.Println(c)
	fmt.Printf("%T", c)
	*/

	/*
	var isFalse bool = true
	fmt.Printf(string(isFalse)) // cannot convert isFalse (variable of type bool) to string
	*/
}
```

```
2
float64
```
