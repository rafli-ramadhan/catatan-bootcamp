# Function vs Procedure

Bedanya function dan procedure adalah function mengembalikkan suatu nilai, sementara procedure tidak.

## Contoh _code_

```go
package main

import (
	"fmt"
)

func main() {
	Introduction("Adi", "programmer", 1, 23)
}

func Introduction(name string, job string, experience, age int) {
	fmt.Printf(`
	    Hello, Iam %s,
		I was an %s,
		I have %d experience
		and I am %d old.
	`, name, job, experience, age)
}
```

```
Hello, Iam Adi,
		I was an programmer,
		I have 1 experience
		and I am 23 old.
```
