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

```go
package main
 
import "fmt"
 
func main() {
	for _, v := range "Golang is Programming Language" {
		fmt.Print(v)
	}

	fmt.Println()
	str := "Golang is Programming Language"
	for i := 1; i < len(str); i++ {
		fmt.Print(str[i])
	}
}
```



Reference:

{% embed url="https://www.golangprograms.com/for-range-loops.html" %}
