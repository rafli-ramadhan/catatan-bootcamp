# Time Since

Time since merupakan fungsi untuk memperoleh durasi waktu dari sejak fungsi time.Now() di inisiasi ke suatu variabel.

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	start := time.Now()
	time.Sleep(5*time.Second)
	fmt.Println(time.Since(start).Seconds(), "seconds")
}
```

```
5.0095269 seconds
```
