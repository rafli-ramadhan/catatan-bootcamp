# Context WithValue, WithDeadline, WithTimeout, WithCancel, Done

WithValue -> Untuk membuat child atau percabangan context

WithCancel -> Untuk mengakhiri context

WithDeadline (waktu diakhiri) -> Untuk mengakhiri context dengan deadline waktu sekarang + beberapa waktu.

```
time.Now().Add(5*Second) // durasi waktu sekarang + 5 detik
```

WithTimeout (durasi) -> Untuk mengakhiri context mirip with deadline -> Context akan jalan sampai waktu tertentu.

Done -> Untuk cek apakah context sudah selesai atau belum

## WithValue

```go
package main

import(
    "context"
    "fmt"
)

func main() {
    value := map[string]interface{}{
        "1":        "member_01",
        "2":        "member_02",
        "isActive": true,
    }
    background := context.Background()
    child := context.WithValue(background, "key-1", value)
    todo := context.TODO()

    fmt.Println(background)
    fmt.Println(child)
    fmt.Println(child.Value("key-1"))
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
	fmt.Println(deadline)

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
2023-03-29 08:01:00.50954036 +0000 UTC m=+0.001151960
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

Cancel broadcast -> mengcancel seluruh context.

```go
ctx, cancel := context.WithCancel(ctx)

go doAnother(ctx)

cancel()
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
