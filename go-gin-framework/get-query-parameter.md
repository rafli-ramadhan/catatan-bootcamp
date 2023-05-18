# Get Query Parameter

Untuk get query parameter caranya mirip dengan get request JSON menggunakan method ShouldBin() seperti _code_ dibawah ini.

```go
package main

import (
	"net/http"
	"github.com/gin-gonic/gin"
)

func main() {
	r := gin.Default()
	r.GET("/", Get)
	r.Run(":5000")
}

type User struct {
	UserName string `form:"username"`
	Password string `form:"password"`
}
func Get(ctx *gin.Context) {
	var user User
	if err := ctx.ShouldBind(&user); err != nil {
		ctx.JSON(404, gin.H{
			"status":  http.StatusBadRequest,
			"message": err,
		})
	} else {
		ctx.JSON(200, gin.H{
			"status": http.StatusOK,
			"data":   user,
		})
	}
}

```

<figure><img src="../.gitbook/assets/1 (1).png" alt=""><figcaption></figcaption></figure>
