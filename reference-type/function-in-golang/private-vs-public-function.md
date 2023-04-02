# Private vs Public Function

* Public : bisa dipakai di beberapa function, contoh : func Calculate()&#x20;
* Private : bisa dipakai hanya dalam 1 package yang sama, contoh: func calculate()

Misal kita ingin mengirim beberapa function di beberapa file.go yang mengharuskan mengirim data ke firebase. Public function bisa dipakai untuk kasus ini.

```go
package main

import (
	"fmt"
	"math"
)

// private function
func pythagoras(a int, b int) float64 {
	return math.Sqrt(math.Pow(float64(a), 2) + math.Pow(float64(b), 2))
}

// private function
func pertambahan(a, b int) (hasil int) {
	hasil = a + b
	return
}

func main() {
	hitung1 := pythagoras(3, 4)
	hitung2 := pertambahan(2, 3)
	var penampungFunction func(int, int) float64 = pythagoras
	fmt.Println(hitung1)
	fmt.Println(hitung2)
	fmt.Println(penampungFunction(3,4))

}
```

```
// Output :
5
5
5
```
