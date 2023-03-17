# Function vs Procedure

Bedanya function dan procedure : function mengembalikkan suatu nilai, sementara procedure tidak.

```go
package main

import (
	"fmt"
)

func main() {
	Introduction("Adi", "programmer", 1, 23)
}

// public function
func Introduction(name string, job string, experience, age int) {
	fmt.Printf(`
	    Hello, Iam %s,
		I was an %s,
		I have %d experience
		and I am %d old.
	`, name, job, experience, age)
}
```

