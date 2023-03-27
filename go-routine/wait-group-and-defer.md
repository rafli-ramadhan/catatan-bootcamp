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

func numbers(wg *sync.WaitGroup) {  
    defer wg.Done()
    for i := 1; i <= 5; i++ {
        fmt.Printf("%d ", i)
    }
}

func alphabets(wg *sync.WaitGroup) {
    defer wg.Done()
    for i := 'a'; i <= 'e'; i++ {
        fmt.Printf("%c ", i)
    }
}

func main() {  
    wg := new(sync.WaitGroup)
    wg.Add(2)

    go numbers(wg)
    go alphabets(wg)
    fmt.Println("end")
    
    wg.Wait()
}
```

```
end
a b c d e 1 2 3 4 5
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
