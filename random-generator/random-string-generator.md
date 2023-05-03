# Random String Generator

```go
package main

import (
    "fmt"
    "math/rand"
    "time"
)

func main() {
  fmt.Println(randomString(50))
}

func randomString(length int) string {
    randomizer := rand.New(rand.NewSource(time.Now().Unix()))
    letters := []rune("abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ")

    b := make([]rune, length)
    for i := range b {
        b[i] = letters[randomizer.Intn(len(letters))]
    }

    return string(b)
}
```

```
lfXUHvhqsqkwBgLtQjdglktxgQdOPHGYKAZiiEznFwSsDfJiaq
```
