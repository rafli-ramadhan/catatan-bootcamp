# Slice Get Value from Array

Slice dapat dibuat dengan mengambil value dari suatu array seperti contoh di bawah ini.

```go
package main

import "fmt"

func main() {
	arr := [5]int{1, 2, 3, 4, 5}
	slice := arr[1:4]
	fmt.Println(slice)
	fmt.Println(len(slice))
	fmt.Println(cap(slice))

	slice = append(slice, 5, 6)
	fmt.Println(slice)
	fmt.Println(len(slice))
	fmt.Println(cap(slice))
}
```

```
[2 3 4]
3
4
[2 3 4 5 6]
5
8
```
