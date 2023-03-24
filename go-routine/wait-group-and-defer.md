# Wait Group & Defer

Wait Group -> digunakan untuk menunggu go routine.

Defer -> mengakhiri eksekusi suatu statement tepat sebelum blok fungsi selesai. akan selalu dieksekusi di akhir.

```go
sync.WaitGroup()
```

```go
package main
  
import (
    "fmt"
    "sync"
)
  
func test1(wg *sync.WaitGroup) {
    defer wg.Done()
    fmt.Println("test 1")
  
}
  
func test2(wg *sync.WaitGroup) {
    defer wg.Done()
    fmt.Println("test 2")
}

func main() {
    wg := new(sync.WaitGroup)
    wg.Add(2)

    go test1(wg)
    go test2(wg)

    wg.Wait()
}

```

```
test 2
test 1
```
