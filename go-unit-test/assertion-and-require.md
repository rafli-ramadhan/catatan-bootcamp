# Assertion & Require

**Assert** -> jika pengecekan gagal, maka assert akan memanggil Fail(), artinya eksekusi unit test akan tetap dilanjutkan.

**Require** -> jika pengecekan gagal, maka assert akan memanggil FailNow(), artinya eksekusi unit test akan tetap dilanjutkan.

```bash
go get github.com/stretchr/testify
```

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
	return "Hello " + name
}

```

## Assertion

main\_test.go

```go
package main

import (
	"testing"
	"github.com/stretchr/testify/assert"
)

func TestSayHi(t *testing.T) {
	// sub test
	t.Run("Test-1", func(t *testing.T) {
		result := SayHi("Amar")
		assert.Equal(t, "Hello Andi", result)
	})
	t.Run("Test-2", func(t *testing.T) {
		result := SayHi("Andi")
		assert.Equal(t, "Hello Andi", result)
	})
	t.Run("Test-3", func(t *testing.T) {
		result := SayHi("Umar")
		assert.Equal(t, "Hello Andi", result)
	})
}

```

```
PS D:\bootcamp-go\go-unit-test> go test -v -run TestSayHi
=== RUN   TestSayHi
=== RUN   TestSayHi/Test-1
    main_test.go:11:
                Error Trace:    D:/bootcamp-go/go-unit-test/main_test.go:11
                Error:          Not equal:
                                expected: "Hello Andi"
                                actual  : "Hello Amar"

                                Diff:
                                --- Expected
                                +++ Actual
                                @@ -1 +1 @@
                                -Hello Andi
                                +Hello Amar
                Test:           TestSayHi/Test-1
=== RUN   TestSayHi/Test-2
=== RUN   TestSayHi/Test-3
    main_test.go:19:
                Error Trace:    D:/bootcamp-go/go-unit-test/main_test.go:19
                Error:          Not equal:
                                expected: "Hello Andi"
                                actual  : "Hello Umar"

                                Diff:
                                --- Expected
                                +++ Actual
                                @@ -1 +1 @@
                                -Hello Andi
                                +Hello Umar
                Test:           TestSayHi/Test-3
--- FAIL: TestSayHi (0.01s)
    --- FAIL: TestSayHi/Test-1 (0.00s)
    --- PASS: TestSayHi/Test-2 (0.00s)
    --- FAIL: TestSayHi/Test-3 (0.00s)
FAIL
exit status 1
FAIL    unit-testing    0.395s
```

## Require

```go
func Equal(t TestingT, expected interface{}, actual interface{}, msgAndArgs ...interface{}) {
	if h, ok := t.(tHelper); ok {
		h.Helper()
	}
	if assert.Equal(t, expected, actual, msgAndArgs...) {
		return
	}
	t.FailNow()
}
```

main\_test.go

```go
package main

import (
	"testing"
	"github.com/stretchr/testify/require"
)

func TestSayHi(t *testing.T) {
	t.Run("Test-1", func(t *testing.T) {
		result := SayHi("Amar")
		require.Equal(t, "Hello Andi", result, "Input Not Andi")
	})
	t.Run("Test-2", func(t *testing.T) {
		result := SayHi("Andi")
		require.Equal(t, "Hello Andi", result, "Input Andi")
	})
	t.Run("Test-3", func(t *testing.T) {
		result := SayHi("Umar")
		require.Equal(t, "Hello Andi", result, "Input Not Andi")
	})
}
```

```
PS D:\bootcamp-go\go-unit-test> go test -v -run TestSayHi
=== RUN   TestSayHi
=== RUN   TestSayHi/Test-1
    main_test.go:11:
                Error Trace:    D:/bootcamp-go/go-unit-test/main_test.go:11
                Error:          Not equal:
                                expected: "Hello Andi"
                                actual  : "Hello Amar"

                                Diff:
                                --- Expected
                                +++ Actual
                                @@ -1 +1 @@
                                -Hello Andi
                                +Hello Amar
                Test:           TestSayHi/Test-1
                Messages:       Input Not Andi
=== RUN   TestSayHi/Test-2
=== RUN   TestSayHi/Test-3
    main_test.go:19:
                Error Trace:    D:/bootcamp-go/go-unit-test/main_test.go:19
                Error:          Not equal:
                                expected: "Hello Andi"
                                actual  : "Hello Umar"

                                Diff:
                                --- Expected
                                +++ Actual
                                @@ -1 +1 @@
                                -Hello Andi
                                +Hello Umar
                Test:           TestSayHi/Test-3
                Messages:       Input Not Andi
--- FAIL: TestSayHi (0.01s)
    --- FAIL: TestSayHi/Test-1 (0.00s)
    --- PASS: TestSayHi/Test-2 (0.00s)
    --- FAIL: TestSayHi/Test-3 (0.01s)
FAIL
exit status 1
FAIL    unit-testing    0.499s
```
