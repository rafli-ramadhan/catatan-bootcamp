# Running Sub Test

```go
package main

import (
	"fmt"
	"testing"
	// "github.com/stretchr/testify/assert"
)

func TestSayHi(t *testing.T) {
	t.Run("Test-1", func(t *testing.T) {
		result := SayHi("Amar")
		if result != "Andi" {
			t.Skip("Not Available")
		}
		fmt.Println("Next")
		result = SayHi("Andi")
		if result != "Andi" {
			t.Error("Andi")
		}
	})
	t.Run("Test-2", func(t *testing.T) {
		result := SayHi("Umar")
		if result != "Andi" {
			t.Skip("Not Available")
		}
		fmt.Println("Next")
		result = SayHi("Utsman")
		if result != "Andi" {
			t.Error("Is Not Andi")
		}
	})
}

```

```
PS D:\bootcamp-go\go-unit-test> go test -v -run TestSayHi/Test-1
=== RUN   TestSayHi
=== RUN   TestSayHi/Test-1
    main_test.go:13: Not Available
--- PASS: TestSayHi (0.00s)
    --- SKIP: TestSayHi/Test-1 (0.00s)
PASS
ok      unit-testing    0.293s
PS D:\bootcamp-go\go-unit-test> go test -v -run TestSayHi/Test-2
=== RUN   TestSayHi
=== RUN   TestSayHi/Test-2
    main_test.go:24: Not Available
--- PASS: TestSayHi (0.00s)
    --- SKIP: TestSayHi/Test-2 (0.00s)
PASS
ok      unit-testing    0.290s
```

