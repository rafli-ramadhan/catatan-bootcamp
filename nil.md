# Nil

```go
package main

import (
	"fmt"
)

func Logging(text string) map[string]string {
    if text == "" {
        return nil
    } else {
        return map[string]string{
            "Text": text,
        }
    }
}

func main() {
    if check:= Logging(""); check == nil {
        fmt.Println("Data is empty")
    } else {
        fmt.Println(check)
    }
}
```



```go
package main

import (
    "errors"
    "fmt"
)

func Pembagian(a, b float64) (float64, error) {
    if b == 0 {
        return 0, errors.New("b should not 0")
    } else {
        return a/b, nil
    }
}

func main() {
    result, err := Pembagian(12,0)
    if err != nil {
        fmt.Println(err)         // return interface
        fmt.Println(err.Error()) // return string
    } else {
        fmt.Println(result)
    }
}
```

```
b should not 0
b should not 0
```
