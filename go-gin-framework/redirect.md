# Redirect

Untuk redirect di Gin bisa menggunakan method Redirect() seperti _code_ di bawah ini. Untuk http status yang digunakan bisa pada redirect bisa berupa

* http.StatusMovedPermanently(201) -> resource yang di request telah dipindahkan ke url yang baru.
* http.StatusTemporaryRedirect(307) -> resource untuk sementara dipindahkan ke url lain.
* http.StatusPermanentRedirect(308) -> resource telah dipindahkan ke url lain.

```go
package main

import (
	"net/http"
	"github.com/gin-gonic/gin"
)

func main() {
	r := gin.Default()
	r.GET("/", Redirect)
	r.Run(":5000")
}

func Redirect(ctx *gin.Context) {
	ctx.Redirect(http.StatusPermanentRedirect, "http://www.google.com/")
}

```

<figure><img src="../.gitbook/assets/1 (4).png" alt=""><figcaption></figcaption></figure>
