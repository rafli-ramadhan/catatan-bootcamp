# Infinite Looping

## Contoh _code_ infinite looping

```go
package main
 
import "fmt"
 
func main() {
	i := 3
	for {
		fmt.Print("Test-", i, " ")
		if i == 10 {
			break
		}
		i++
	}
}
```

```
Test-3 Test-4 Test-5 Test-6 Test-7 Test-8 Test-9 Test-10 
```
