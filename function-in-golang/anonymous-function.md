# Anonymous Function

Membuat function secara langsung di variabel atau parameter tanpa harus membuat parameter terlebih dahulu

## 1. Anonymous Function sebagai Variabel

```go
package main

import (
	"fmt"
)

type Filter func(name string) string

func sayHelloWithFilter(name string, filter Filter) {
	nameFiltered := filter(name)
	fmt.Println("Hello", nameFiltered)
}
	
func main() {
	// anonymous function as variable
	filter := func(name string) string {
		if name == "Kucing" {
			return ""
		} else {
			return name
		}
	}
	sayHelloWithFilter("Umar", filter)
	sayHelloWithFilter("Andi", filter)
}
	
```

## 2. Anonymous Function sebagai Parameter

```go
package main

import (
	"fmt"
)

type Filter func(name string) string

func sayHelloWithFilter(name string, filter Filter) {
	nameFiltered := filter(name)
	fmt.Println("Hello", nameFiltered)
}
	
func main() {
	// anonymous function as parameter
	sayHelloWithFilter("Umar", func(name string) string {
		if name == "Kucing" {
			return ""
		} else {
			return name
		}
	})
	sayHelloWithFilter("Andi", func(name string) string {
		if name == "Kucing" {
			return ""
		} else {
			return name
		}
	})
}
	
```



