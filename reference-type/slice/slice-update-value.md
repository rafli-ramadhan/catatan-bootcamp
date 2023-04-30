# Slice Update Value

Untuk memperbaruhi value dengan index tertentu dari suatu slice, dapat langsung diubah seperti contoh di bawah ini.

```go
package main
import "fmt"

func main() {
    a := [5]int{1,2,3,4,5}
    a[2] = 10
    fmt.Println(a)
}
```

```
[1 2 10 4 5]
```

