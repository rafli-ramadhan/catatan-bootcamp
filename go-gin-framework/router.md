# Router

Untuk membuat router bisa menggunakan method sesuai HTTP Verb yang akan dipakai. Contoh untuk GET bisa menggunakan method GET.

```go
package main

import (
	"github.com/gin-gonic/gin"
)

func main() {
	r := gin.Default()

	r.GET("/welcome", welcome)
	r.Run(":5000")
}

func welcome(ctx *gin.Context) {
	ctx.Writer.Write([]byte("success"))
}
```

<figure><img src="../.gitbook/assets/1 (2) (1) (1).png" alt=""><figcaption></figcaption></figure>
