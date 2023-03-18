# Make Slice 2

Make digunakan untuk membuat suatu slice

## Contoh #1&#x20;

```go
package main

import (
	"fmt"
)

func main() {
        slice1 := make([]int, 5, 5)
	fmt.Println(slice2)

	slice2 := make([]string, 5, 5)
	fmt.Println(slice2)

	slice3 := make([]float64, 5, 5)
	fmt.Println(slice3)

	slice4 := make([]bool, 5, 5)
	fmt.Println(slice4)
}
```

```
// Output
[0 0 0 0 0]
[    ]
[0 0 0 0 0]
[false false false false false]
```

## Contoh #2

```go
package main

import (
	"fmt"
)

func main() {
	// make(type, length, capacity)
	a := make([]int, 5)
	fmt.Println("value of a:", a)

	str := make([]string, 5)
	fmt.Println("value of a:", str)

	// str2 := make([3]string, 5)       // -> error
	// fmt.Println("value of a:", str2)

	b := make([]int, 10, 20)
	fmt.Println("value of b:", b)

	c := make([]int, 10, 30)
	fmt.Println("value of c:", c)

	// runtime error: index out of range [5] with length 5
	a[0], a[1], a[2], a[3], a[4], a[5] = 1, 2, 3, 4, 5, 6
	fmt.Println("value of a:", a)
}
```

```
// Output :
value of a: [0 0 0 0 0]
value of a: [    ]
value of b: [0 0 0 0 0 0 0 0 0 0]
value of c: [0 0 0 0 0 0 0 0 0 0]
panic: runtime error: index out of range [5] with length 5
```

