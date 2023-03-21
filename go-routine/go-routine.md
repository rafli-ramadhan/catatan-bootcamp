# Go Routine

Go routine -> untuk menjalakan concurrency di golang -> sifatnya asynchronous -> tidak saling tunggu -> dan secara random.

{% embed url="https://miro.medium.com/v2/resize:fit:1400/1*ylONk4ex9q6IK68C6USRBg.jpeg" %}
[https://miro.medium.com/v2/resize:fit:1400/1\*ylONk4ex9q6IK68C6USRBg.jpeg](https://miro.medium.com/v2/resize:fit:1400/1\*ylONk4ex9q6IK68C6USRBg.jpeg)
{% endembed %}

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
