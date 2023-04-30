# Make Slice

Make digunakan untuk membuat suatu slice. Fungsi make memiliki 3 input parameter yaitu data type, length dan capacity, dimana capacity harus lebih dari length (capacity > length).

## Contoh _code_

```go
package main

import (
	"fmt"
)

func main() {
        slice1 := make([]int, 5, 5)
	fmt.Println(slice2)

	slice2 := make([]string, 5, 5)
	fmt.Println(slice2)

	slice3 := make([]float64, 5, 5)
	fmt.Println(slice3)

	slice4 := make([]bool, 5, 5)
	fmt.Println(slice4)
}
```

```
[0 0 0 0 0]
[    ]
[0 0 0 0 0]
[false false false false false]
```

## Capacity < Length

<pre class="language-go"><code class="lang-go"><strong>package main
</strong>import "fmt"

func main() {
    a := make([]int, 5, 2)
    fmt.Println(a)
}
</code></pre>

```
invalid argument: length and capacity swapped
```

## Input Value lebih dari Length Slice

```go
package main
import "fmt"

func main() {
    a := make([]int, 5, 6)
    a[0], a[1], a[2], a[3], a[4], a[5] = 1, 2, 3, 4, 5, 6
    fmt.Println(a)
}
```

```
panic: runtime error: index out of range [5] with length 5
```

## Kekurangan Make Slice

Saat kita menginputkan suatu value ke dalam slice yang melebihi length dari slice, capacity dari slice tersebut akan menjadi 2 kali lipatnya. Cotohnya seperti _code_ dibawah ini. Slice s yang awalnya tidak mempunyai value, kemudian di isi value secara bertahap menggunakan _looping_. Lalu di print kapasitas dan length dari slice tersebut.

```go
package main
import "fmt"

func main() {
    s := make([]int, 0, 3)
    fmt.Println(s)
    for i := 0; i < 20; i++ {
        s = append(s, i)
        fmt.Printf("cap %v, len %v, %p\n", cap(s), len(s), s)
    }
}
```

```
[]
cap 3, len 1, 0xc000018018
cap 3, len 2, 0xc000018018
cap 3, len 3, 0xc000018018
cap 6, len 4, 0xc000014270
cap 6, len 5, 0xc000014270
cap 6, len 6, 0xc000014270p
cap 12, len 7, 0xc00005e060
cap 12, len 8, 0xc00005e060
cap 12, len 9, 0xc00005e060
cap 12, len 10, 0xc00005e060
cap 12, len 11, 0xc00005e060
cap 12, len 12, 0xc00005e060
cap 24, len 13, 0xc00007a000
cap 24, len 14, 0xc00007a000
cap 24, len 15, 0xc00007a000
cap 24, len 16, 0xc00007a000
cap 24, len 17, 0xc00007a000
cap 24, len 18, 0xc00007a000
cap 24, len 19, 0xc00007a000
cap 24, len 20, 0xc00007a000
```

## Informasi tambahan

Suatu slice misalkan s disimpan dengan _memory address_ yang berbeda dengan value-value di dalam array tersebut.

```go
package main
import "fmt"

func main() {
    s := make([]int, 0, 3)
    for i := 0; i < 5; i++ {
        s = append(s, i)
        fmt.Printf("cap %v, len %v, %p\n", cap(s), len(s), s)
        for i := range s {
            val := &i
            fmt.Println(val)
        }
    }
}
```

```
cap 3, len 1, 0xc000018018
0xc00001a050
cap 3, len 2, 0xc000018018
0xc00001a058
0xc00001a058
cap 3, len 3, 0xc000018018
0xc00001a060
0xc00001a060
0xc00001a060
cap 6, len 4, 0xc000014270
0xc00001a068
0xc00001a068
0xc00001a068
0xc00001a068
cap 6, len 5, 0xc000014270
0xc00001a070
0xc00001a070
0xc00001a070
0xc00001a070
0xc00001a070
```
