# t.Fail, t.FailNow, t.Error & t.Fatal, t.Skip

* t.Fail() -> menggagalkan unit test, namun tetap melanjutkan eksekusi unit test -> Unit test tersebut dianggap gagal.

```go
func (c *common) Fail() {
	if c.parent != nil {
		c.parent.Fail()
	}
	c.mu.Lock()
	defer c.mu.Unlock()
	// c.done needs to be locked to synchronize checks to c.done in parent tests.
	if c.done {
		panic("Fail in goroutine after " + c.name + " has completed")
	}
	c.failed = true
}
```

* t.FailNow() -> menggagalkan unit test saat ini juga, tanpa melanjutkan eksekusi unit test.

```go
func (c *common) FailNow() {
	c.checkFuzzFn("FailNow")
	c.Fail()

	// Calling runtime.Goexit will exit the goroutine, which
	// will run the deferred functions in this goroutine,
	// which will eventually run the deferred lines in tRunner,
	// which will signal to the test loop that this test is done.
	//
	// A previous version of this code said:
	//
	//	c.duration = ...
	//	c.signal <- c.self
	//	runtime.Goexit()
	//
	// This previous version duplicated code (those lines are in
	// tRunner no matter what), but worse the goroutine teardown
	// implicit in runtime.Goexit was not guaranteed to complete
	// before the test exited. If a test deferred an important cleanup
	// function (like removing temporary files), there was no guarantee
	// it would run on a test failure. Because we send on c.signal during
	// a top-of-stack deferred function now, we know that the send
	// only happens after any other stacked defers have completed.
	c.mu.Lock()
	c.finished = true
	c.mu.Unlock()
	runtime.Goexit()
}
```

* t.Error() -> log (print) error -> otomatis memanggil function Fail(), sehingga mengakibatkan unit test dianggap gagal -> eksekusi unit test akan tetap berjalan sampai selesai.

```go
func (c *common) Error(args ...any) {
	c.checkFuzzFn("Error")
	c.log(fmt.Sprintln(args...))
	c.Fail()
}
```

* t.Fatal() mirip dengan Error() -> otomatis memanggil FailNow() -> sehingga mengakibatkan eksekusi unit test berhenti.

```go
func (c *common) Fatal(args ...any) {
	c.checkFuzzFn("Fatal")
	c.log(fmt.Sprintln(args...))
	c.FailNow()
}
```

* t.Skip() -> skip suatu unit test + return argument

```go
func (c *common) Skip(args ...any) {
	c.checkFuzzFn("Skip")
	c.log(fmt.Sprintln(args...))
	c.SkipNow()
}
```

* t.SkipNow() -> Skip suatu unit test + exit

```go
func (c *common) SkipNow() {
	c.checkFuzzFn("SkipNow")
	c.mu.Lock()
	c.skipped = true
	c.finished = true
	c.mu.Unlock()
	runtime.Goexit()
}
```

## Implementasi Fatal

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
			t.Fatal("Not Andi")
		}
		fmt.Println("Next")
		result = SayHi("Andi")
		if result != "Andi" {
			t.Fatal("Andi")
		}
	})
}

```

```
PS D:\bootcamp-go\go-unit-test> go test -v -run TestSayHi
=== RUN   TestSayHi
=== RUN   TestSayHi/Test-1
    main_test.go:13: Not Andi
--- FAIL: TestSayHi (0.00s)
    --- FAIL: TestSayHi/Test-1 (0.00s)
FAIL
exit status 1
FAIL    unit-testing    0.316s
```

## Implementasi Error

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
			t.Error("Not Andi")
		}
		fmt.Println("Next")
		result = SayHi("Andi")
		if result != "Andi" {
			t.Error("Andi")
		}
	})
}

```

```
PS D:\bootcamp-go\go-unit-test> go test -v -run TestSayHi
=== RUN   TestSayHi
=== RUN   TestSayHi/Test-1
    main_test.go:13: Not Andi
Next
    main_test.go:18: Andi
--- FAIL: TestSayHi (0.00s)
    --- FAIL: TestSayHi/Test-1 (0.00s)
FAIL
exit status 1
FAIL    unit-testing    0.374s
```

## Implementasi Skip

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
}

```

```
PS D:\bootcamp-go\go-unit-test> go test -v -run TestSayHi
=== RUN   TestSayHi
=== RUN   TestSayHi/Test-1
    main_test.go:13: Not Available
--- PASS: TestSayHi (0.00s)
    --- SKIP: TestSayHi/Test-1 (0.00s)
PASS
ok      unit-testing    0.270s
```
