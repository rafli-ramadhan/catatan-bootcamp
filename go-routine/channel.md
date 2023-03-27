# Channel

Channel -> digunakan untuk menghubungkan goroutine satu dengan goroutine yang lainnya.

Tugas channel -> mengirim dan menerima data.

```go
package main
  
import "fmt"
  
func test(value chan int) {
    fmt.Println(123 + <-value)
}
func main() {
    fmt.Println("Start")
    value := make(chan int)

    go test(value)
    value <- 25
    
    go test(value)
    value <- 23
    
    fmt.Println("End")
}
```

```
Start
148
146
End
```

```go
package main

import (
    "fmt"
    "math/rand"
)

func getData(value chan int) {
    value1 := rand.Int()
    value <- value1
}

func main() {
    value := make(chan int)
    go getData(value)
    value1 := <- value
    fmt.Println(value1)
}

```

```
5577006791947779410
```
