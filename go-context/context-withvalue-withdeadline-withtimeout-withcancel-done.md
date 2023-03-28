# Context WithValue, WithDeadline, WithTimeout, WithCancel, Done

WithValue -> Untuk menambahkan value

WithCancel -> Untuk mengakhiri context

WithDeadline -> Untuk mengakhiri context dengan deadline waktu tertentu

WithTimeout -> Untuk mengakhiri context mirip with deadline, tapi dengan format yang lebih sederhana

Done -> Untuk cek apakah context sudah selesai atau belum

## WithValue

```go
package main

import(
    "context"
    "fmt"
)

func main() {
    value := map[string]string{
        "1": "one",
        "2": "two",
    }
    background := context.Background()
    child := context.WithValue(background, "value", value)
    todo := context.TODO()

    fmt.Println(background)
    fmt.Println(child)
    fmt.Println(child.Value("value"))
    fmt.Println(todo)
}
```

```
context.Background
context.Background.WithValue(type string, val <not Stringer>)
map[1:one 2:two]
context.TODO
```

## WithDeadline

```go
package main

import (
	"context"
	"fmt"
	"time"
)

func main() {
	deadline := time.Now().Add(1 * time.Millisecond)
	ctx, cancel := context.WithDeadline(context.Background(), deadline)
	defer cancel()

	select {
	case <-time.After(1 * time.Second):
		fmt.Println("overslept")
	case <-ctx.Done():
		fmt.Println(ctx.Err())
	}
}
```

```
context deadline exceeded
```

## With Timeout

```go
package main

import (
	"context"
	"fmt"
	"time"
)

func main() {
	ctx, cancel := context.WithTimeout(context.Background(), 1 * time.Millisecond)
	defer cancel()

	select {
	case <-time.After(1 * time.Second):
		fmt.Println("overslept")
	case <-ctx.Done():
		fmt.Println(ctx.Err())
	}
}

```

```
context deadline exceeded
```

## With Cancel

```go
ctx, cancelCtx := context.WithCancel(ctx)

go doAnother(ctx)

cancelCtx()
```

## Done

```go
select {
case <-time.After(1 * time.Second):
	fmt.Println("overslept")
case <-ctx.Done():
	fmt.Println(ctx.Err())
}
```
