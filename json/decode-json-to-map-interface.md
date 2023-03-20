# Decode JSON to Map Interface

JSON -> Map interface

```go
package main

import (
    "encoding/json"
    "fmt"
)

func main() {
    var jsonString = `{"Name": "john wick", "Age": 27}`
    var jsonData = []byte(jsonString)

    var user map[string]interface{}
    // json -> struct
    var err = json.Unmarshal(jsonData, &user)
    if err != nil {
        fmt.Println(err.Error())
        return
    }

    fmt.Println(user)
}
```

```
map[Age:27 Name:john wick]
```
