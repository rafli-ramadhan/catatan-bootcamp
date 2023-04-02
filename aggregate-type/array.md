# Array

**Kekurangan** -> hanya bisa di isi value sesuai dengan length yang telah di deklarasikan.

## Create an Array

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
	// names[3] = "Test4" // -> error
	fmt.Printf("%s %s %s \n", names[0], names[1], names[2])

	var values = [3]int{12, 13, 14}
	fmt.Println(values)

	var strings = [3]string{"Test1", "Test2", "Test3"}
	fmt.Println(strings)
}
```

## Array Memory Addresses, Different from Their Own Values

```go
package main
import "fmt"

func main() {
    a := [10]int{1,2,3,4,5,6,7,8,9,10}
	b := &a
    fmt.Printf("%p\n", b)
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
