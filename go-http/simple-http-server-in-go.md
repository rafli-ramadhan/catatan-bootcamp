# HTTP Server

Berikut _code_ untuk membuat HTTP server dengan native golang (tanpa framework).

```go
package main

import (
	"fmt"
	"net/http"
)

func main() {
	var handler http.HandlerFunc = func(w http.ResponseWriter, r *http.Request) {
		fmt.Fprintf(w, "Server running")
	}

	server := http.Server{
		Addr:   "localhost:5000",
		Handler: handler,
	}

	fmt.Println("Server running")
	err := server.ListenAndServe()
	if err != nil{
		panic(err.Error())
	}
}
```

Open localhost:5000

{% embed url="https://pkg.go.dev/net/http#Server.Handler" %}
