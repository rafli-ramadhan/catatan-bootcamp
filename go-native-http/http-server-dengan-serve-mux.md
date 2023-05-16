# HTTP Server dengan Serve Mux

HTTP server juga bisa dibuat dengan menggunakan serve mux. Untuk menggunakan serve mux perlu keyword NewServeMux. New di awal keyword tersebut untuk mengembalikan struct serve mux yang sifatnya masih private (tidak bisa diakses di luar package) di dalam package net/http.

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
