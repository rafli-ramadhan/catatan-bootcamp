# Decode JSON to Struct

JSON -> Struct

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
    var jsonString = `{"Name": "john wick", "Age": 27}`
    var jsonData = []byte(jsonString)

    var user User
    // json -> struct
    var err = json.Unmarshal(jsonData, &user)
    if err != nil {
        fmt.Println(err.Error())
        return
    }

    fmt.Println(user)
    fmt.Println(user.Name)
    fmt.Println(user.Age)
}
```

```
{andri 21}
andri
21
```
