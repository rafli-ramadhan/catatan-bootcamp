# Encode Struct to JSON

Struct -> JSON

```go
package main

import (
    "encoding/json"
    "fmt"
)

type User struct {
    Name string `json:"Name"`
    Age  int
}

func main() {
    users := []User{{"john wick", 27}, {"ethan hunt", 32}}
    var jsonData, err = json.Marshal(users)
    if err != nil {
        fmt.Println(err.Error())
        return
    }
    
    var jsonString = string(jsonData)
    fmt.Println(jsonString)
}
```

```
[{"Name":"john wick","Age":27},{"Name":"ethan hunt","Age":32}]
```
