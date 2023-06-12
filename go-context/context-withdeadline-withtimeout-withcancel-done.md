# Context WithDeadline, WithTimeout, WithCancel, Done

Context memiliki beberapa jenis diantarnya:

* WithCancel digunakan untuk mengakhiri context.
* WithDeadline (waktu diakhiri) digunakan untuk mengakhiri context dengan deadline waktu sekarang + beberapa waktu kedepan.
* WithTimeout (durasi) digunakan untuk menjalankan suatu code sampai waktu tertentu.
* Done -> Untuk cek apakah context sudah selesai atau belum

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
