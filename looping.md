# Looping For

Looping merupakan cara untuk mengulangi urutan data dari suatu string, array, map dan string.&#x20;

## Contoh _code_ looping sederhana

```go
package main
 
import "fmt"
 
func main() {
	i := 1
	for ; i <= 10; i++ {
		fmt.Println(i)
	}
 
	i = 1
	for i <= 10 {
		fmt.Println(i)
		i++
	}
 
	for i := 1; ; i++ {
		fmt.Println(i)
		if i == 10 {
			break
		}
	}
}
```

```
1
2
3
4
5
6
7
8
9
10
1
2
3
4
5
6
7
8
9
10
1
2
3
4
5
6
7
8
9
10
```

## Contoh _code_ looping string

Looping di string di Golang menghasilkan value dengan tipe data rune bukan byte.

```go
package main

import "fmt"

func main() {
	str := "Hello, world!"
	for i, c := range str {
		fmt.Printf("str[%d] = %c type %T\n", i, c, c)
	}
}

```

```go
str[0] = H type int32
str[1] = e type int32
str[2] = l type int32
str[3] = l type int32
str[4] = o type int32
str[5] = , type int32
str[6] =   type int32
str[7] = w type int32
str[8] = o type int32
str[9] = r type int32
str[10] = l type int32
str[11] = d type int32
str[12] = ! type int32
```

## Contoh looping for dengan operator update +=

```go
package main

import "fmt"

func main() {
    i := 0
    for i < 10 {
        fmt.Println(i)
        i += 2
    }
}
```

```
0
2
4
6
8
```

Reference:

{% embed url="https://stackoverflow.com/questions/58635507/rune-vs-byte-ranging-over-string" %}

{% embed url="https://www.golangprograms.com/for-range-loops.html" %}
