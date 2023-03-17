# Assignment Operator

Assignment operator -> ++, --, +=, -=, \*=, /=

```go
package main

import (
	"fmt"
)

func main() {
	var a int = 2
	a += 4
	fmt.Println(a)

	a -= 3
	fmt.Println(a)

	a *= 2
	fmt.Println(a)

	a /= 3
	fmt.Println(a)

	a %= 2
	fmt.Println(a)

	var b float64 = 2.2
	b += 5
	fmt.Println(b)

	b -= 4
	fmt.Println(b)

	b *= 3
	fmt.Println(b)

	b /= 2
	fmt.Println(b)

	// b %= 2.0 // -> invalid operation: operator % not defined for b (variable of type float64)

	var c string = "test1"
	c += "test2"
	fmt.Println(c)

	// c -= "test3" // -> invalid operation: operator - not defined for c (variable of type string)

	// c *= "test3" // -> invalid operation: operator * not defined for c (variable of type string)

	// c /= "test3" // -> invalid operation: operator / not defined for c (variable of type string)

	var d bool = true
	fmt.Println(d)
	// d += false // -> invalid operation: operator + not defined for d (variable of type bool)

	// d /= false // -> invalid operation: operator / not defined for d (variable of type bool)
}
```
