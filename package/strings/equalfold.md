# EqualFold

Case insensitive

```go
package main

import(
    "fmt"
    "strings"
)

func main() {
    fmt.Println(strings.EqualFold("Test", "test"))
    fmt.Println(strings.EqualFold("Test", "Test"))
}
```

```
true
true
```
