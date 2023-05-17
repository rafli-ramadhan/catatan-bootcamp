# Pointer in Method

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
