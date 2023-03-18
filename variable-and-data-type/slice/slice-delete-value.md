# Slice Delete Value

Format append -> append(\[]int, ...int) -> append(slice, value) -> variadic function

```go
package main
import "fmt"

func main() {
    a := []int{1,2,3,4,5}
    a = append(a[:2], a[2+1:]...)
    fmt.Println(a)
}
```

```
[1 2 4 5]
```

Kodingan di atas sama dengan kodingan di bawah ini :

```go
package main
import "fmt"

func main() {
    a := []int{1,2,3,4,5}
    a = append(a[:2], []int{4,5}...)
    fmt.Println(a)
}
```

```go
package main
import "fmt"

func main() {
    a := []int{1,2,3,4,5}
    a = append(a[:2], 4, 5)
    fmt.Println(a)
}
```

