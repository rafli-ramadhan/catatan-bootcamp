# HTTP Server using ServeMux in Go

ServeMux -> harus diubah jadi -> NewServeMux -> karena parameter di struct serve mux private.

HandlerFunc -> syaratnya harus ada response dan request.

```go
package main

import (
	"fmt"
	"net/http"
)

func main() {
	mux := http.NewServeMux()

	var handlerMain http.HandlerFunc = func(write http.ResponseWriter, result *http.Request) {
		fmt.Println("Server running")
		fmt.Fprintf(write, "Server running")
	}
	var handlerTest http.HandlerFunc = func(write http.ResponseWriter, result *http.Request) {
		fmt.Println("Server running")
		fmt.Fprintf(write, "Test")
	}

	mux.HandleFunc("/main", handlerMain)
	mux.HandleFunc("/test", handlerTest)

	server := http.Server{
		Addr:   "localhost:5000",
		Handler: mux,
	}

	err := server.ListenAndServe()
	if err != nil{
		panic(err.Error())
	}
}
```
