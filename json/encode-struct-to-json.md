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
    users := []User{{"andi", 21}, {"andre", 20}}
    // struct -> json
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
[{"Name":"andi","Age":21},{"Name":"andre","Age":20}]
```
