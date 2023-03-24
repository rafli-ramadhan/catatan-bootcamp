# Channel



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
