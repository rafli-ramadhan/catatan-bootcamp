# Type Declaration

Type declaration digunakan untuk membuat variabel baru (alias) dari tipe data yang sudah ada (string, int, float, bool, array, slice, map, struct, interface atau function).

## Contoh _code_

```go
package main

import (
	"fmt"
)

func main() {
	type NoKTP string
	var KTPNumber NoKTP = "43284234928347293"
	fmt.Println(KTPNumber)

	type IsValid bool
	var isValid IsValid = true
	fmt.Println(isValid)
}
```

```
43284234928347293
true
```
