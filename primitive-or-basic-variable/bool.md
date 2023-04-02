# Bool

Default -> False

```go
package main

import "fmt"

var IsTrue bool

func main() {
    fmt.Println(IsTrue)
    fmt.Println(!IsTrue)
    if IsTrue {             // -> if IsTrue == true
        fmt.Println(IsTrue)
    }
    if !IsTrue {            // -> if IsTrue == false
        fmt.Println(IsTrue)
    }
}
```

```
false
true
false
```
