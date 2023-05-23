# Marshal (Go Object -> JSON)

Marshal merupakan cara untuk mengubah object dalam Golang menjadi JSON string. Object tersebut dapat berupa map\[string]interface atau struct.

## Contoh _code_ encode dari struct menjadi JSON string

```go
package main

import (
    "encoding/json"
    "fmt"
)

type User struct {
    Name string
    Age  int
}

func main() {
    users := []User{
        {"andi", 21}, 
        {"andre", 20}
    }
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



