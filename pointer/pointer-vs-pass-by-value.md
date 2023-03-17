# Pointer vs Pass By Value

Pass by value (default golang) -> saat kita mengirim suatu variabel ke variabel lain, fungsi atau method, yang dikirim sebenarnya adalah duplikasinya. Duplikasi variabel pada variabel lain, fungsi atau method yang dituju akan membuat memory address baru.

Kelebihan pointer -> memungkinkan penggunaan memory address seminimal mungkin -> suatu variabel bisa di inisiasi dengan value variabel lain, tanpa membuat memory address baru -> disebut reference -> variabel 1 dan variabel 2 punya value yang sama dan memory address yang sama.

Kekurangan pointer -> jika nilai variabel yang me-reference variabel lain diubah, variabel lain tersebut juga akan berubah.

```go
package main

import (
    "fmt"
)

type Address struct{
    City     string
    Province string
    Country  string
}

func main() {
    name1 := "member_1"
    name1 = ChangeName(name1)
    fmt.Println(name1)
}

func ChangeName(name string) string {
    name = "member_2"
    return name
}
```

```
member_2
```

