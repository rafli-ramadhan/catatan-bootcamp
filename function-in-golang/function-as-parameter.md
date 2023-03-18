# Function as Parameter

Function bisa disimpan sebagai value dalam variabel dan bisa digunakan untuk function yang lain.

## Contoh function #1

```go
package main

import (
	"fmt"
)

// function type declaration
type Filter func(name string) string

func sayHelloWithFilter(name string, filter Filter) {
	nameFiltered := filter(name)
	fmt.Println("Hello", nameFiltered)
}

func spamFilter(name string) string {
	if name == "Kucing" {
		return ""
	} else {
		return name
	}
}
	
func main() {
	filter := spamFilter
	sayHelloWithFilter("Alan", filter)
	sayHelloWithFilter("Hana", filter)
}
```

```
// Output :
Hello Alan
Hello Hana
```

```go
package main

import (
	"fmt"
	"strings"
)

// function as parameter
func IsDirty(word string, filterWord func(string) bool) {
	if filterWord(word) {
		fmt.Println("That is dirty word")
	} else {
		fmt.Println("That is not dirty word")
	}
}
	
func main() {
	// anonymous function
	filterWord := func(word string) bool {
		if strings.Contains(word, "fuck") {
			return true
		} else {
			return false
		}
	}

	IsDirty("hi", filterWord)
	IsDirty("fuck", filterWord)
}

```

```
// Output :
That is not dirty word
That is dirty word
```

