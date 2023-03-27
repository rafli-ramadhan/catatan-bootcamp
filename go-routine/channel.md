# Channel

**Fungsi** -> tempat komunikasi data secara synchronous oleh go routine -> saat melakukan pengiriman data, go routine akan terblok sampai ada yang menerima data tersebut (blocking).

**Karakteristik** -> hanya bisa menerima 1 tipe data, secara default hanya bisa menampung 1 data, jika tidak digunakan harus di close atau bisa menyebabkan memory leak.

**Channel In -> Mengirim data**

**Channel Out -> Menerima data**

```go
package main
  
import "fmt"
  
func test(value chan int) {
    fmt.Println(123 + <-value)
}
func main() {
    fmt.Println("Start")
    value := make(chan int)

    go test(value)
    value <- 25
    
    go test(value)
    value <- 23
    
    fmt.Println("End")
}
```

```
Start
148
146
End
```

```go
package main

import (
    "fmt"
    "math/rand"
)

func getData(value chan int) {
    value1 := rand.Int()
    value <- value1
}

func main() {
    value := make(chan int)
    go getData(value)
    value1 := <- value
    fmt.Println(value1)
}

```

```
5577006791947779410
```
