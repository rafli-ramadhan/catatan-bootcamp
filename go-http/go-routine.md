# Go Routine

Go routine -> menjalakan go routine,&#x20;





```go
package main

import (
	"fmt"
	"runtime"
)

func print(num int, message string) {
	fmt.Println("Start")
    for i := 0; i < num; i++ {
        fmt.Println((i + 1), message)
    }
	fmt.Println("End")
}

func main() {
    runtime.GOMAXPROCS(3)

    go print(5, "halo")
	go print(5, "hai")
    print(5, "apa kabar")

    var input string
    fmt.Scanln(&input)
}
```

```
1 apa kabar
2 apa kabar
3 apa kabar
4 apa kabar
5 apa kabar
End
Start
1 halo
2 halo
3 halo
4 halo
5 halo
End
Start
1 hai
2 hai
3 hai
4 hai
5 hai
End
```
