# Mutex (Lock & Unlock)



```go
package main

import (  
    "fmt"
    "sync"
)

func numbers(wg *sync.WaitGroup, m *sync.Mutex) {  
    defer wg.Done()
    m.Lock()
    for i := 1; i <= 5; i++ {
        fmt.Printf("%d ", i)
    }
    m.Unlock()
}

func alphabets(wg *sync.WaitGroup, m *sync.Mutex) {
    defer wg.Done()
    m.Lock()
    for i := 'a'; i <= 'e'; i++ {
        fmt.Printf("%c ", i)
    }
    m.Unlock()
}

func main() {  
    wg := new(sync.WaitGroup)
    wg.Add(2)
    m := new(sync.Mutex)

    go numbers(wg, m)
    go alphabets(wg, m)
    fmt.Println("end")
    
    wg.Wait()
}
```

```
end
a b c d e 1 2 3 4 5
```
