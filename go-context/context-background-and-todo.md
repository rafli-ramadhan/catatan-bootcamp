# Context Background & TODO

Membuat context kosong, tidak pernah dibatalkan, tidak pernah time out dan tidak ada value apapun.

Digunakan di main function atau di test atau untuk proses request.

```
context.Background()
```

Membuat context kosong mirip dengan context background. TODO digunakan saat belum jelas context apa yang ingin digunakan.

```
context.TODO()
```

```go
package main

import(
    "context"
    "fmt"
)

func main() {
    background := context.Background()
    fmt.Println(background)
    todo := context.TODO()
    fmt.Println(todo)
}
```

```
context.Background
context.TODO
```
