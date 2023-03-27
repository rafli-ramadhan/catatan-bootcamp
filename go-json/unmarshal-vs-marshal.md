# Unmarshal vs Marshal

Umarshal (Decode) dan Marshal (Encode) -> bisa untuk Int, String, Bool, Slice, Struct dan Map String Interface.

## Marshal (...-> JSON) & Unmarshal (JSON -> ...) Int

```go
package main

import (
    "encoding/json"
    "fmt"
)

func main() {
    jsonData, _ := json.Marshal(123)
    fmt.Println(string(jsonData))
}
```

```
123 // -> JSON
```

```go
package main

import (
    "encoding/json"
    "fmt"
)

func main() {
    var jsonString = `2`
    var jsonData = []byte(jsonString)

    var data int

    var err = json.Unmarshal(jsonData, &data)
    if err != nil {
        fmt.Println(err.Error())
        return
    }

    fmt.Println(data)
}
```

```
123
```

## Marshal (...-> JSON) & Unmarshal (JSON -> ...) String

```go
package main

import (
    "encoding/json"
    "fmt"
)

func main() {
    jsonData, _ := json.Marshal("test")
    fmt.Println(string(jsonData))
}
```

```
"test" // -> JSON
```

```go
package main

import (
    "encoding/json"
    "fmt"
)

func main() {
    var jsonString = `"test"`
    var jsonData = []byte(jsonString)

    var data string

    var err = json.Unmarshal(jsonData, &data)
    if err != nil {
        fmt.Println(err.Error())
        return
    }

    fmt.Println(data)
}
```

```
test
```

## Marshal (...-> JSON) & Unmarshal (JSON -> ...) Bool

```go
package main

import (
    "encoding/json"
    "fmt"
)

func main() {
    jsonData, _ := json.Marshal(true)
    fmt.Println(string(jsonData))
}
```

```
true // -> JSON
```

```go
package main

import (
    "encoding/json"
    "fmt"
)

func main() {
    var jsonString = `true`
    var jsonData = []byte(jsonString)

    var data bool
    // json -> struct
    var err = json.Unmarshal(jsonData, &data)
    if err != nil {
        fmt.Println(err.Error())
        return
    }

    fmt.Println(data)
}
```

```
true
```

## Marshal (...-> JSON) & Unmarshal (JSON -> ...) Slice

```go
package main

import (
    "encoding/json"
    "fmt"
)

func main() {
    jsonData, _ := json.Marshal([]string{"test 1", "test 2", "test 3"})
    fmt.Println(string(jsonData))
}
```

```
["test 1","test 2","test 3"] // -> JSON
```

```go
package main

import (
    "encoding/json"
    "fmt"
)

func main() {
    var jsonString = `["test 1", "test 2", "test 3"]`
    var jsonData = []byte(jsonString)

    var data []string
    // json -> struct
    var err = json.Unmarshal(jsonData, &data)
    if err != nil {
        fmt.Println(err.Error())
        return
    }

    fmt.Println(data)
}
```

```
[test 1 test 2 test 3]
```
