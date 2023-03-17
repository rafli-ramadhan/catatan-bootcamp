# Logic Operator

Logical -> And, Or, Not

```go
package main

import (
	"fmt"
)

func main() {
   var left bool = false
   var right bool = true

   var leftAndRight bool = left && right
   var leftOrRight bool = left || right
   var leftReserve bool = !left
   
   fmt.Printf("left && right \t(%t)\n", leftAndRight)
   fmt.Printf("left || right \t(%t)\n", leftOrRight)
   fmt.Printf("!left \t\t(%t)\n", leftReserve)
}
```

