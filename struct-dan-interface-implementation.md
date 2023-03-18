# Struct dan Interface Implementation

```go
package main

import "fmt"

// struct handler dengan method test
type Handler struct{
    b B // -> variabel b tipe data B
    c C // -> variabel c tipe data C
}

func (h *Handler) Test() {
    h.b.Print()
    h.c.Print()
}

// repository
type B struct {
}

func (b *B) Print() {
    fmt.Println("Berhasil")
}

type C struct {
}

func (c *C) Print() {
    fmt.Print("Berhasil 2")
}

// implementasi
func main() {
    // anonymus function
    repo1 := NewRepo1()
    repo2 := NewRepo2()
    handler := NewHandler(*repo1, *repo2)
    handler.Test()
}

// NewRepo2 return memory address struct B
func NewRepo1() *B {
    return &B{
    }
}

// NewRepo2 return memory address struct C
func NewRepo2() *C {
    return &C{
    }
}

// NewHandler return memory address struct Handler
func NewHandler(input1 B, input2 C) *Handler {
    return &Handler{
        b: input1,
        c: input2,
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

