# Make Slice

Format -> make(data type, length, capacity), **capacity > length**.

```go
package main
import "fmt"

func main() {
    a := make([]int, 5, 5)
    fmt.Println(a)
}
```

```
[0 0 0 0 0]
```

```go
package main
import "fmt"

func main() {
    a := make([]int, 5, 2)
    fmt.Println(a)
}
```

```
invalid argument: length and capacity swapped
```

```go
package main
import "fmt"

func main() {
    a := make([]int, 5, 6)
    a[0], a[1], a[2], a[3], a[4], a[5] = 1, 2, 3, 4, 5, 6
    fmt.Println(a)
}
```

```
panic: runtime error: index out of range [5] with length 5
```
