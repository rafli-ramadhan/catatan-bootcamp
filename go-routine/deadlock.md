# Deadlock

Deadlock -> kondisi dimana go routine saling tunggu.

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
