# Function dengan Return Multiple Value

Function dengan return multiple value memungkinkan output lebih dari 1 value.

## Contoh _code_ 1

```go
package main

import (
	"fmt"
)
	
func main() {
	result1, result2 := sayHi("Dawam")
	fmt.Println(result1, result2)
}

func sayHi(name string) (string, string) {
	return fmt.Sprintf("Hi %s nice to meet you.", name), fmt.Sprintf("Welcome. ")
}

```

```
Hi Dawam nice to meet you. Welcome.
```

## Contoh _code_ 2 dengan mengabaikan 1 return value

```go
package main

import (
	"fmt"
)
	
func main() {
	result1, _ := sayHi("Dawam")
	fmt.Println(result1)
}

func sayHi(name string) (string, string) {
	return fmt.Sprintf("Hi %s nice to meet you.", name), fmt.Sprintf("Welcome. ")
}

```

```
Hi Dawam nice to meet you.
```
