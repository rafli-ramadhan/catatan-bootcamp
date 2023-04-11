# Table Test

Table test -> digunakan untuk test secara dinamis -> menyediakan data beruba slice yang berisi parameter dan ekspektasi hasil dari unit test.

main.go

```go
package main

import (
	"fmt"
)

func main() {
	result := SayHi("Utsman")
	fmt.Println(result)
}

func SayHi(name string) string {
	return name
}

```

main\_test.go

```go
package main

import (
	"testing"
	// "github.com/stretchr/testify/assert"
)

type TestTable struct {
	input		 string
	expected 	 bool
	subtestName  string
	errorMessage string
}

func TestSayHi2(t *testing.T) {
	var tableTest []TestTable = []TestTable{
		{
			input: "Andi",
			expected: true,
			subtestName: "Test-1",
			errorMessage: "Is Andi",
		},
		{
			input: "Umar",
			expected: false,
			subtestName: "Test-2",
			errorMessage: "Is Not Andi",
		},
		{
			input: "Utsman",
			expected: false,
			subtestName: "Test-3",
			errorMessage: "Is Not Andi",
		},
	}

	for _, v := range tableTest {
		t.Run(v.subtestName, func(t *testing.T) {
			if result := SayHi(v.input); result != "Andi" {
				t.Error("Not Andi")
			}
		})
	}
}
```

```
PS D:\bootcamp-go\go-unit-test> go test -v -run TestSayHi2
=== RUN   TestSayHi2
=== RUN   TestSayHi2/Test-1
=== RUN   TestSayHi2/Test-2
    main_test.go:40: Not Andi
=== RUN   TestSayHi2/Test-3
    main_test.go:40: Not Andi
--- FAIL: TestSayHi2 (0.00s)
    --- PASS: TestSayHi2/Test-1 (0.00s)
    --- FAIL: TestSayHi2/Test-2 (0.00s)
    --- FAIL: TestSayHi2/Test-3 (0.00s)
FAIL
exit status 1
FAIL    unit-testing    0.384s
```
