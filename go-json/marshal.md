# Marshal

## Marshal Int (Int -> JSON)

```go
package main

import (
    "encoding/json"
    "fmt"
)

func main() {
    a, _ := json.Marshal(123)
    fmt.Println(string(a))
}
```

```
123
```

## Marshal String (String -> JSON)

```go
package main

import (
    "encoding/json"
    "fmt"
)

func main() {
    a, _ := json.Marshal("test")
    fmt.Println(string(a))
}
```

```
"test"
```

## Marshal Bool (Bool-> JSON)

```go
package main

import (
    "encoding/json"
    "fmt"
)

func main() {
    a, _ := json.Marshal(true)
    fmt.Println(string(a))
}
```

```
true
```

## Marshal Slice (Slice -> JSON)

```go
package main

import (
    "encoding/json"
    "fmt"
)

func main() {
    a, _ := json.Marshal([]string{"test 1", "test 2", "test 3"})
    fmt.Println(string(a))
}
```

```
["test 1","test 2","test 3"]
```



```
// Some code
```

```
// Some code
```

