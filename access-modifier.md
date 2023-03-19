# Access Modifier (Public or Private)

Menentukan access modifier cukup dengan nama function atau variabel.\
Nama variabel atau function besar -> bisa diakses di package lain

```go
package main

import (
    "fmt"
)

// public variable -> bisa diakses di package lain
var ErrInvalid   string = "invalid"
const StatusTrue bool   = true

// private variable -> tidak bisa diakses di package lain
var errInvalid   string = "invalid"
const statusTrue bool   = true

// public function -> bisa diakses di package lain
func Calculate() {}

// private function -> tidak bisa diakses di package lain
func calculate() {}
```
