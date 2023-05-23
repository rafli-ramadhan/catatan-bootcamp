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

	var handler1 http.HandlerFunc = func(w http.ResponseWriter, r *http.Request) {
		fmt.Fprintf(w, "Test Main")
	}
	var handler2 http.HandlerFunc = func(w http.ResponseWriter, r *http.Request) {
		fmt.Fprintf(w, "Test")
	}

	mux.HandleFunc("/main", handler1)
	mux.HandleFunc("/test", handler2)

	server := http.Server{
		Addr:   "localhost:5000",
		Handler: mux,
	}

	fmt.Println("Server running")
	err := server.ListenAndServe()
	if err != nil{
		panic(err.Error())
	}
}
```
