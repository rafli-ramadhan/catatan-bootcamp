# Array



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
