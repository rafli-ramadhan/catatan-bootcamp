# HTTP Server

Berikut _code_ untuk membuat HTTP server dengan native golang (tanpa framework).

## Server dengan http.Handler

```go
package main

import (
	"fmt"
	"net/http"
)

type handler1 struct{}
	
func (h handler1) ServeHTTP(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintf(w, "Test Handler")
}

func main() {
	server := http.Server{
		Addr:   "localhost:5000",
		Handler: handler1{},
	}

	fmt.Println("Server running")
	err := server.ListenAndServe()
	if err != nil{
		panic(err.Error())
	}
}
```

## Server dengan http.HandlerFunc

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
