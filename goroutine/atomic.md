# Atomic

```go
package main

import (
	"fmt"
	"sync/atomic"
)

type Person struct {
	name string
	age  int
}

func main() {
	var person atomic.Value
	person.Store(Person{name: "John", age: 30})
	fmt.Println("Initial Person:", person.Load())

	person.Store(Person{name: "Jane", age: 25})
	fmt.Println("New Person:", person.Load())
}
```

