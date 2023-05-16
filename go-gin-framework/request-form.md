# Request Form

Untuk request form bisa digunakan method PostForm seperti _code_ dibawah ini

```go
package main

import (
	"net/http"

	"github.com/gin-gonic/gin"
)

func main() {
	r := gin.Default()
	r.POST("/form", PostForm)
	r.Run(":5000")
}

func PostForm(c *gin.Context) {
	username := c.PostForm("username")
	password := c.PostForm("password")

	c.JSON(200, gin.H{
		"status":	http.StatusOK,
		"data":		map[string]interface{}{
			"username": username,
			"password": password,	
		},
	})
}
```

<figure><img src="../.gitbook/assets/req.png" alt=""><figcaption></figcaption></figure>
