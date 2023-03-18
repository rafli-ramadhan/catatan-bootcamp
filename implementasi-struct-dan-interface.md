# Implementasi Struct dan Interface

```go
package main

import "fmt"

type A struct{
    a int
}
func (a *A) Print() {
    fmt.Println(a.a)
}

func main() {
    NewHandler(2).Print()
}

func NewHandler(input int) *A {
    return &A{
        a: input,
    }
}
```

```
2
```

Kodingan di atas memiliki output yang sama dengan kodingan di bawah ini

```go
package main

import "fmt"

type A struct{
    a int
}
func (a A) Print() {
    fmt.Println(a.a)
}

func main() {
    NewHandler(2).Print()
}

func NewHandler(input int) A {
    return A{
        a: input,
    }
}
```

