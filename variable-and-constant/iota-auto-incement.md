---
description: by Mochamad Rafli Ramadhan
---

# Iota (Auto incement)

## Iota

Iota digunakan untuk mendeklarasikan beberapa constant yang membutuhkan auto increment

```go
package main

import (
	"fmt"
)

func main() {
	const (
		int2 = 2 + iota*2
		int3
		int4
	)
	fmt.Println(int2, int3, int4)  // Result -> 2, 4, 6 

	// Contoh untuk deklarasi variabel hari menjadi integer dari 1 sampai 7
	const (
		Monday = 1 + iota
		Tuesday
		Wednesday
		Thursday
		Friday
		Saturday
		Sunday
	)
	fmt.Println(Monday)

	// Contoh untuk deklarasi variabel bulan menjadi integer dari Januari sampai Desember
	const (
		January = 1 + iota
		February
		March
		April
		May
		June
		July
		August
		September
		October
		November
		December
	)
	fmt.Println(January)
}
```



