# Get Current Time By Location

```go
package main

import (
    "fmt"
    "time"
)

func main() {
    now := time.Now()
    fmt.Println(now)
	loc, err := time.LoadLocation("Asia/Jakarta")
	if err != nil {
		panic(err)
	}
	fmt.Println(now.In(loc).Year())
	fmt.Println(now.In(loc).Month())
	fmt.Println(now.In(loc).Day())
	fmt.Println(now.In(loc).Format("02/01/2006 03:04 PM"))
	fmt.Println(now.In(loc).Format("03:04 PM"))
	fmt.Println(now.In(loc).Format("15:04"))
}
```

```
2023-03-23 07:30:07.947319446 +0000 UTC m=+0.000053890
2023
March
23
23/03/2023 02:30 PM
02:30 PM
14:30
```
