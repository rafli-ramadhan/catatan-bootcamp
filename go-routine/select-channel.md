# Select Channel

Penerapan select pada channel

```go
package main

import (
    "errors"
    "fmt"
    "sync"
)

var wg sync.WaitGroup

func main() {
    success := make(chan bool, 1)
	errCh := make(chan error, 1)

    wg.Add(1)

	go func() {
		defer wg.Done()
		err := errors.New("there is an error")
		errCh <- err
	}()

	wg.Wait()
    success <- true

	select {
	case err := <-errCh:
		fmt.Println(err)
	case <- success:
		fmt.Println("success")
	}
}
```

```
D:\go-server>go run .
error there is an error

D:\go-server>go run .
success

D:\go-server>go run .
success

D:\go-server>go run .
there is an error
```
