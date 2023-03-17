# Pointer di Method

```go
package main

import (
    "fmt"
)

type Man struct{
    Name string
}

func (m Man) Married() {
    fmt.Println("Mr. " + m.Name)
}

func main() {
    member_01 := Man{"member_01"}
    member_01.Married()
}
```

```
Mr. member_01
```
