# Go Routine vs Synchronous

Synchronous diwakili dengan fmt.Println()

```go
package main

import (
	"fmt"
	"time"
)

func main() {
    fmt.Println("start")
    duration := time.Now()

    go func() {
        fmt.Println("test 1", time.Since(duration))
        go func() {
            fmt.Println("test 1.a", time.Since(duration))
        }()
            
        go func() {
            fmt.Println("test 1.b", time.Since(duration))
        }()
    
        go func() {
            fmt.Println("test 1.c", time.Since(duration))
        }()
        
        fmt.Println("test 2", time.Since(duration))
	}()
    
    fmt.Println("end", time.Since(duration))
    time.Sleep(2*time.Second)
    fmt.Println("end", time.Since(duration))
}
```

```
start
end 14.316µs
test 1 80.584µs
test 2 118.592µs
test 1.c 128.012µs
test 1.a 143.493µs
test 1.b 156.41µs
end 2.000573491s
```

```go
package main

import (
	"fmt"
	"time"
)

func main() {
    fmt.Println("start")
    duration := time.Now()

    go func() {
        go func() {
            fmt.Println("test 1.a", time.Since(duration))
        }()
            
        go func() {
            fmt.Println("test 1.b", time.Since(duration))
        }()
    
        go func() {
            fmt.Println("test 1.c", time.Since(duration))
        }()
        
        fmt.Println("test 2", time.Since(duration))
	}()
    
    fmt.Println("end", time.Since(duration))
    time.Sleep(2*time.Second)
    fmt.Println("end", time.Since(duration))
}
```

```
start
end 15.274µs
test 2 113.019µs
test 1.c 152.354µs
test 1.a 169.296µs
test 1.b 184.646µs
end 2.001080916s
```
