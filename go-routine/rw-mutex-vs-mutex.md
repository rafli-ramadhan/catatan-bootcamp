# RW Mutex vs Mutex

RW Mutex -> Digunakan untuk supaya beberapa function dapat membaca data yang sama secara bersamaan.

## Mutex Only

```go
package main
 
import (
    "fmt"
    "sync"
)

var wg sync.WaitGroup
var m sync.Mutex
 
func print(i, v int) {
    rw.RLock()
    fmt.Printf("iterasi-%d %d\n", i, v)
    rw.RUnlock()
    wg.Done()
}

func main() {
    var v int = 0
 
    for i := 1; i <= 100; i++ {
        wg.Add(2)
	var i = i

        go func() {
            m.Lock()
            v++
            m.Unlock()
            wg.Done()
        }()

	print(i, v)
    }
    
    wg.Wait()
    fmt.Println("\nFinished", v)
}
```

```
...
iterasi-90 87
iterasi-91 87
iterasi-92 91
iterasi-93 91
iterasi-94 91
iterasi-95 91
iterasi-96 91
iterasi-97 91
iterasi-98 91
iterasi-99 91
iterasi-100 91

Finished 100
```

## RW Mutex

## Contoh #1

```go
package main
 
import (
    "fmt"
    "sync"
)

var wg sync.WaitGroup
var m sync.Mutex
var rw sync.RWMutex
 
func print(i, v int) {
    rw.RLock()
    fmt.Printf("iterasi-%d %d\n", i, v)
    rw.RUnlock()
    wg.Done()
}

func main() {
    var v int = 0
 
    for i := 1; i <= 100; i++ {
        wg.Add(2)
	var i = i

        go func() {
            m.Lock()
            v++
            m.Unlock()
            wg.Done()
        }()

	print(i, v)
    }
    
    wg.Wait()
    fmt.Println("\nFinished", v)
}
```

```
...
iterasi-91 90
iterasi-92 91
iterasi-93 92
iterasi-94 93
iterasi-95 94
iterasi-96 95
iterasi-97 96
iterasi-98 97
iterasi-99 98
iterasi-100 99

Finished 100
```

## Contoh #2

```go
package main

import (
    "fmt"
    "sync"
)

var (
    sharedResource int
    mutex          sync.Mutex
    rwmu           sync.RWMutex
)

func main() {
    // Example using a sync.Mutex
    var wg sync.WaitGroup
    for i := 0; i < 10; i++ {
        wg.Add(1)
        go func() {
            mutex.Lock()
            defer mutex.Unlock()
            sharedResource++
            wg.Done()
        }()
    }
    wg.Wait()
    fmt.Printf("Final value using Mutex: %d\n", sharedResource)

    // Example using a sync.RWMutex
    var rwg sync.WaitGroup
    for i := 0; i < 10; i++ {
        rwg.Add(1)
        go func() {
            rwmu.Lock()
            defer rwmu.Unlock()
            sharedResource++
            rwg.Done()
        }()
    }
    for i := 0; i < 10; i++ {
        rwg.Add(1)
        go func() {
            rwmu.RLock()
            defer rwmu.RUnlock()
            fmt.Printf("Read value using RWMutex: %d\n", sharedResource)
            rwg.Done()
        }()
    }
    rwg.Wait()
    fmt.Printf("Final value using RWMutex: %d\n", sharedResource)
}
```
