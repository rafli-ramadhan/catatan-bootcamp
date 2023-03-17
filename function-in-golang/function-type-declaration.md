# Function Type Declaration

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
