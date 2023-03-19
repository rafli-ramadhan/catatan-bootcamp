# Struct Comparation

Membandingkan apakah struct 1 dan struct 2 sama atau tidak.

```go
package main

import (
	"fmt"
)

func main() {
	type User struct{
		name string
		age  int
	}

	var user User = User{}
	fmt.Println(user)
	var user2 User = User{}
	if user == user2 {
		fmt.Printf("true")
	}
}
```

```
{ 0}
truet
```
