---
description: Slice dan Array
---

# Length and Capactiy

```go
package main

import (
	"fmt"
)

func main() {
	arr := [5]int{1,2,3,4,5}
	slice := arr[2:4] // upper breaker max = 6

	fmt.Println(arr)
	fmt.Println(slice)
	fmt.Println(cap(slice))
	slice = append(slice, 12)
	
	fmt.Println(arr)
	fmt.Println(slice)
	fmt.Println(cap(slice))
	slice = append(slice, 13)

	fmt.Println(arr)
	fmt.Println(slice)
	fmt.Println(cap(slice))
	slice = append(slice, 14)

	fmt.Println(arr)
	fmt.Println(slice)
	fmt.Println(cap(slice))
}
```
