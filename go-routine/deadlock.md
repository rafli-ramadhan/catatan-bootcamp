# Deadlock

Deadlock -> kondisi dimana go routine saling tunggu -> alhasil tidak ada go routine yang berjalan.

```go
package main

import "fmt"

func main() {
        ch := make(chan int)
        // channel in
        ch <- 1
        // channel out
        fmt.Println(<-ch)
}
```

```
fatal error: all goroutines are asleep - deadlock!
goroutine 1 [chan send]:
main.main()
/tmp/uv1yQwKDgN.go:7 +0x37
exit status 2
```

```go
package main
  
import "fmt"

func f(value chan int) {
    result := 100 + <- value
    fmt.Printf("%d ", result)
}

func main() {
    fmt.Println("Start")
    value := make(chan int)

    for i := 0; i < 10; i++ {
        value <- i
        go f(value)
    }
    
    fmt.Println("\nEnd")
    close(value)
}
```

```
Start
fatal error: all goroutines are asleep - deadlock!

goroutine 1 [chan send]:
main.main()
        D:/go-server/main.go:15 +0x9e
exit status 2
```
