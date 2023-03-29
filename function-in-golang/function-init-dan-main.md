# Function Init dan Main

Di golang func main dieksekusi saat perintah `go run` di jalankan. Sementara func Init tidak menerima parameter atau me-return suatu value. Baik ada atau tidak ada func main, func init akan selalu dijalankan saat go run .

```go
package main

import "fmt"

var WhatIsThe = 5

func init() {
	WhatIsThe = 0
	fmt.Println("init")
}

func main() {
	if WhatIsThe == 0 {
		fmt.Println(0)
	}
	fmt.Println("main")
}
```

```
init
0
main
```
