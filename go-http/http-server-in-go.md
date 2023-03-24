# Simple HTTP Server in Go

```go
package main

import (
	"fmt"
	"net/http"
)

func main() {
	var handler http.HandlerFunc = func(write http.ResponseWriter, result *http.Request) {
		fmt.Println("Server running")
		fmt.Fprintf(write, "Server running")
	}

	server := http.Server{            // -> type data -> struct 
		Addr:   "localhost:5000", // -> string
		Handler: handler,
	}

	err := server.ListenAndServe()
	if err != nil{
		panic(err.Error())
	}
}
```

Open localhost:5000

{% embed url="https://pkg.go.dev/net/http#Server.Handler" %}
