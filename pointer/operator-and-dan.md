# Operator & dan \*

& -> untuk reference dari suatu data dari suatu memory -> memberi tahu alamat suatu variabel.\
\* -> menampilkan data tersebut sesuai dengan tipe data aslinya (melihat datanya).\
Variabel biasa kalau ingin di ubah jadi pointer pakai &.

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
    name2 := &name1          // reference from memory address name
    fmt.Println(name1)
    fmt.Println(*name2)      // menampilkan variabel name1 yang me-reference variabel name harus dengan operator *
    fmt.Println(&name1)      // check memory address variabel name1
    fmt.Println(name2)       // check memory address variabel name2

    *name2 = "member_2"      // assign variabel name1 dengan nilai baru yang me-reference variabel name dengan tipe string
    fmt.Println(name1)
    fmt.Println(*name2)
    fmt.Println(&name1)      // check memory address
    fmt.Println(name2)       // check memory address
}
```

```
member_1
member_1
0xc00003e230
0xc00003e230
member_2
member_2
0xc00003e230
0xc00003e230
```

