# Type Declaration

Membuat variabel baru dari tipe variabel yang sudah ada (string, int, float, bool, array, slice, map, struct, function).

```go
package main

import (
	"fmt"
)

func main() {
	// static type: store data only for one data type / tipe data yang tidak dapat diubah.
	type NoKTP string
	var KTPNumber NoKTP = "43284234928347293"
	fmt.Println(KTPNumber)

	type IsValid bool
	var isValid IsValid = true
	fmt.Println(isValid)
}
```
