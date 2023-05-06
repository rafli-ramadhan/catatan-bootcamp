# Contoh Implementasi Struct and Interface

Berikut adalah contoh implementasi struct dan interface

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
    fmt.Println("Berhasil 1")
}

type C struct {
}

func (c *C) Print() {
    fmt.Print("Berhasil 2")
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

// implementasi
func main() {
    // anonymus function
    repo1 := NewRepo1()
    repo2 := NewRepo2()
    handler := NewHandler(*repo1, *repo2)
    handler.Test()
}
```

```
Berhasil 1
Berhasil 2
```
