# Tag

Tag -> anotasi setelah deklarasi variabel di struct.&#x20;

```go
package main

import "fmt"

type User struct {
	Name string `example:"name"`
}

func (u *User) String() string {
	return fmt.Sprintf("name : %s", u.Name)
}

func main() {
	user := &User{
		Name: "Andi",
	}
	fmt.Println(user)
}
```

```
name : Andi
```
