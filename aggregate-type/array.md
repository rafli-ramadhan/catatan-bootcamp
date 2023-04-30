# Array

Array merupakan jenis tipe data aggregate di Golang yang mampu menampung beberapa value dengan tipe data yang sama dengan jumlah (length) tertentu. Kekurangan dari array adalah hanya bisa di isi value sesuai dengan length yang telah di deklarasikan.

## Contoh _code_

```go
package main

import (
	"fmt"
)

func main() {
	var names [3]string
	names[0] = "Test1"
	names[1] = "Test2"
	names[2] = "Test3"
	// names[3] = "Test4" -> error karena melebihi length dari array
	fmt.Printf("%s %s %s \n", names[0], names[1], names[2])

	var values = [3]int{12, 13, 14}
	fmt.Println(values)
}
```

```
Test1 Test2 Test3 
[12 13 14]
```

## Informasi tambahan

Suatu variabel array misalkan arr1 disimpan dengan _memory address_ yang berbeda dari value-value di dalam array tersebut. Sebagai contoh _code_ di bawah ini, variabel arr1 disimpan pada _memory address_ 0xc000014280, sementara value dalam array arr1 yaitu 1, 2, 3, dst disimpan dalam memory address 0xc00000e088.

```go
package main
import "fmt"

func main() {
    arr1 := [10]int{1,2,3,4,5,6,7,8,9,10}
	arr2 := &arr1
    fmt.Printf("%p\n", arr2)
    for i := range a {
        val := &i
        fmt.Println(val)
    }
}
```

```
0xc000014280
0xc00000e088
0xc00000e088
0xc00000e088
0xc00000e088
0xc00000e088
0xc00000e088
0xc00000e088
0xc00000e088
0xc00000e088
0xc00000e088
```
