# Slice Delete Value

Untuk menghapus suatu value dengan index tertentu di slice dapat menggunakan fungsi append. Dimana append memiliki format append(slice, ...value). Parameter kedua dalam fungsi append merupakan variadic function, yang berarti append dapat menerima lebih dari 2 input.

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

Kodingan di atas sama memiliki algoritma yang sama dengan kodingan di bawah ini :

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

