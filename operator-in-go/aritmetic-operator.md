# Aritmetic Operator

Aritmatik -> <, >, =&#x20;

```go
package main

import (
	"fmt"
)

func main() {
	var a = 2
	var b = 3
	var value = a + b*2/1%2
	fmt.Println(value)

	value++
	fmt.Println(value)

	fmt.Println("2"+"2")
	fmt.Println(2+2)
	fmt.Println(9/4)

	var c float64 = 9
	var d float64 = 4
	var result float64
	result = c/d

	fmt.Println(result)
	
	var result2 = 9.0/4.0
	fmt.Println(result2)

	fmt.Println(9%2)
}
```

```
2
3
22
4
2
2.25
2.25
1
```
