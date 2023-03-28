# Pool

Pool -> implementasi design pattern bernama object pool pattern.&#x20;

Design pattern Pool -> digunakan untuk menyimpan data.

Untuk menggunakan datanya, kita bisa mengambil dari Pool.

Setelah selesai menggunakan datanya, kita bisa menyimpan kembali ke Pool.

Implementasi Pool di Go-Lang ini sudah aman dari problem race condition.

```go
var pool sync.Pool
```

```go
package main
 
import (
    "fmt"
    "sync"
    "time"
)

var wg sync.WaitGroup
var pool sync.Pool

func main() {
    var v int
    pool.Put(v)
    pool.Put(2)
    pool.Put(3)
    pool.Put(4)
    pool.Put(5)
    pool.Put(6)
    pool.Put(7)
    pool.Put(8)
    pool.Put(9)
    pool.Put(10)

    for i := 0; i < 10; i++ {
        data := pool.Get()
        fmt.Printf("%d ", data)
    }

    time.Sleep(3 * time.Millisecond)    
}
```

```
0 10 9 8 7 6 5 4 3 2
```

