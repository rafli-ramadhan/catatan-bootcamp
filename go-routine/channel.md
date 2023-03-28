# Channel

**Fungsi** -> tempat komunikasi data secara synchronous oleh go routine -> saat melakukan pengiriman data, go routine akan terblok sampai ada yang menerima data tersebut (blocking).

**Karakteristik** -> hanya bisa menerima 1 tipe data, secara default hanya bisa menampung 1 data, jika tidak digunakan harus di close atau bisa menyebabkan memory leak.

**Channel In -> Mengirim data**

**Channel Out -> Menerima data**

```go
package main
  
import "fmt"
  
func test(value chan int) {
    result := 100 + <- value
    fmt.Printf("%d ", result)
}

func main() {
    fmt.Println("Start")
    value := make(chan int)

    for i := 0; i < 10; i++ {
        go test(value)
        value <- i
    }
    fmt.Println("\nEnd")
}
```

```
Start
100 101 102 103 104 105 106 107 108 109 
End
```

```go
package main
  
import "fmt"
  
func test(value chan int) {
    result := 100 + <- value
    value <- result
}

func main() {
    fmt.Println("Start")
    value := make(chan int)

    for i := 0; i < 10; i++ {
        go test(value)
        value <- i
        result := <- value
        fmt.Printf("%d ", result)
    }
    fmt.Println("\nEnd")
}
```

```
Start
100 101 102 103 104 105 106 107 108 109 
End
```
