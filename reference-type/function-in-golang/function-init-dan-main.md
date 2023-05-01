# Function Init dan Main

Di golang function main dieksekusi saat perintah `go run` di jalankan. Sementara function Init tidak menerima parameter atau me-return suatu value. Baik ada atau tidak ada function main, function init akan selalu dijalankan saat `go run` .

## Contoh _code_

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
