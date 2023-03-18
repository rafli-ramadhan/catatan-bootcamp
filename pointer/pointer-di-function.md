# Pointer in Function

```go
package main

import (
    "fmt"
)

type Address struct{
    City     string
    Province string
    Country  string
}

func main() {
    name1 := "member_1"
    name2 := &name1
    ChangeName(name2)
    fmt.Println(name1)
}

func ChangeName(name *string) {
    *name = "member_2"
}
```

```
member_2
```

