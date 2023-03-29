# Deadlock

Deadlock -> kondisi dimana go routine saling tunggu -> alhasil tidak ada go routine yang berjalan.

## Contoh kasus

Jika channel in (pengirim) di inisisasi terlebih dahulu dan channel out (penerima) di inisiasi setelah channel in -> deadlock.

Jika channel out (penerima) di inisisasi terlebih dahulu dan channel in (pengirim) di inisiasi setelah channel out -> ada output yang ditampilkan.&#x20;

```go
package main

import "fmt"

func main() {
        ch := make(chan int)
        // channel in (pengirim)
        ch <- 1
        // channel out (penerima)
        go func() {
            result := <- ch
            fmt.Println(result)
        }()
}
```

```
fatal error: all goroutines are asleep - deadlock!
goroutine 1 [chan send]:
main.main()
/tmp/uv1yQwKDgN.go:7 +0x37
exit status 2
```

```go
package main

import "fmt"

func main() {
        ch := make(chan int)
        // channel out (penerima)
        go func() {
            result := <- ch
            fmt.Println(result)
        }()
        // channel in (pengirim)
        ch <- 1
}
```

```
1
```

```go
package main
  
import "fmt"

func f(value chan int) {
    result := 100 + <- value
    fmt.Printf("%d ", result)
}

func main() {
    fmt.Println("Start")
    value := make(chan int)

    for i := 0; i < 10; i++ {
        // channel in (pengirim)
        value <- i
        // channel out (penerima)
        go f(value)
    }
    
    fmt.Println("\nEnd")
    close(value)
}
```

```
Start
fatal error: all goroutines are asleep - deadlock!

goroutine 1 [chan send]:
main.main()
        D:/go-server/main.go:15 +0x9e
exit status 2
```

```go
package main
  
import "fmt"

func f(value chan int) {
    result := 100 + <- value
    fmt.Printf("%d ", result)
}

func main() {
    fmt.Println("Start")
    value := make(chan int)

    for i := 0; i < 10; i++ {
        //channel out (penerima)
        go f(value)
        // channel in (pengirim)
        value <- i
    }
    
    fmt.Println("\nEnd")
    close(value)
}
```

```
Start
100 101 102 103 104 105 106 107 108 109 
End
```
