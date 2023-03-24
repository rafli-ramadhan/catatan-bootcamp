# Switch

```go
package main

import (
    "fmt"
)

func choose(value int) {
	switch(value) {
	case 1:
		fmt.Println(1)
	case 2:
		fmt.Println(2)
	case 3:
		fmt.Println(3)
	}
}

func main() {
	choose(1)
	choose(2)
}
```
