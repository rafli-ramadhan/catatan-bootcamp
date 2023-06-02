# Pointer in Method

## Contoh _code_ 1

```go
package main

import (
    "fmt"
)

type Man struct{
    Name string
}

func (m *Man) Test1() {
    m.Name = "member_02"
    fmt.Println(*m)
}

func (m Man) Test2() {
    m.Name = "member_03"
    fmt.Println(m)
}

func (m Man) Test3() {
    fmt.Println(m)
}

func main() {
    member_01 := Man{"member_01"}
    fmt.Println(member_01)
    member_01.Test1()
    member_01.Test2()
    member_01.Test3()
    
    fmt.Println(member_01)
}
```

```
{member_01}
{member_02}
{member_03}
{member_02}
{member_02}
```

## Contoh code 2

```go
package main
import "fmt"

type str string

func (s *str) Update1() {
	*s = "member_02"
}

func (s str) Update2() {
	s = "member_03"
}

func main() {
	var name str = "member_01"
	name.Update1()
	name.Update2()
	fmt.Println(name)
}


```

```
member_02
```

## Contoh _code_ 3

```go
package main
import "fmt"

type User struct {
	Name string
}

func (m *User) Update1() {
	m.Name = "member_02"
}

func (m User) Update2() {
	m.Name = "member_03"
}

func main() {
	user := User{"member_01"}
	user.Update1()
	user.Update2()
	fmt.Println(user)
}
```

```
{member_02}
```
