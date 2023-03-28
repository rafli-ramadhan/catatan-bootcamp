# Race Condition

Race condition -> beberapa thread mencoba untuk mengakses dan memanipulasi data yang sama secara bersamaan.

```go
package main
 
import (
    "fmt"
    "sync"
)
 
func f(v *int) {
    *v++
}
 
func main() {
 
    var wg sync.WaitGroup
    var v int = 0
 
    for i := 0; i < 1000; i++ {
        wg.Add(1)
        go f(&v, &wg)
        wg.Done()
    }
 
    wg.Wait()
    fmt.Println("Finished", v)
}
```

```
Finished 987
```
