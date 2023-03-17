---
description: If else digunakan untuk percabangan yang tidak butuh banyak case.
---

# If Else



````
```go
package main

import "fmt"

func main() {
    name1 := "Rafli"
    if name1 == "Rafli" {
        fmt.Printf("Hello %v \n", name1)
 	} else if name1 == "Umar" {
		fmt.Println("Hello")
	} else {
		fmt.Println("Hi, Boleh kenalan?")
	}

	// if else with variable temporary
	if name2 := "Rafli"; name2 == "Rafli" {
        fmt.Printf("Hello %v", name2)
 	} else if name2 == "Umar" {
		fmt.Println("Hello")
	} else {
		fmt.Println("Hi, Boleh kenalan?")
	}

	if len := len(name1); len > 5 {
		fmt.Println("\nNama terlalu panjang")
	} else {
		fmt.Println("\nNama sudah benar")
	}	
}

```
````

