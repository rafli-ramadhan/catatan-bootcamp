# Default Variable

```go
package main

import(
	"fmt"
)

func Hello() {
	fmt.Println("Hello")
}

func main() {
	// aggregate -> menampung value dari tipe data yang sudah ada
	var b [3]int
	fmt.Println(b)							// [0, 0, 0]

	type User struct {
		Name  string
		Age   int
	}
	var c User
	fmt.Println(c)						// { 0}
	fmt.Println(c == User{})				// true

	var a []int
	fmt.Println(a)						// []
	fmt.Println(a == nil)					// nil

	type error interface {
		Error() string
	}

	var d error
	fmt.Println(d == nil)					// true

	var e map[string]int					
	fmt.Println(e == nil)					// true

	var g map[string]int = map[string]int{} 		// false
	fmt.Println(g == nil)
}
```

```
[0 0 0]
{ 0}
true
[]
true
true
true
false
```
