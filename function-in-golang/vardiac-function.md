# Vardiac Function

Variadic -> untuk memungkinkan fungsi dengan input parameter lebih dari 1 data (varargs) dengan tipe data yang sama.

Parameter terkahir dari sebuah function dapat dibuat variadic.

Keunggulannya ->tidak perlu membuat array atau slice terlebih dahulu, kita bisa langsung mengirim datanya dan dipisahkan dengan tanda koma.

```go
package main

import (
	"fmt"
)

func main() {
	total := sumAll(10, 20, 30, 40, 50, 60, 70)
	fmt.Println(total)

	numbers := []int{10, 20, 30, 40, 50, 60, 70}
	fmt.Println(sumAll(numbers...))

	// numbers := [7]int{10, 20, 30, 40, 50, 60, 70} -> can not use array
	// fmt.Println(sumAll(numbers...))
}

// the input will be a slice
func sumAll(numbers ...int) int {
	total := 0
	for _, value := range numbers {
		total += value // total = total + value
	}
	return total
}
```



