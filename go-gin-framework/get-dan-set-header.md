# Get dan Set Header

Untuk request header di Gin bisa menggunakan method GetHeader() dan untuk set header baru di response bisa menggunakan method Header(). Contohnya seperti _code_ dibawah ini.

```go
package main

import (
	"fmt"
	"net/http"
)

func main() {
	mux := http.NewServeMux()
	mux.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
		// get header from request
		key := r.Header.Get("key")
		// add header in request
		r.Header.Add("username", "test")
		// add new header
		w.Header().Add("Data", key)
		// update existing header
		w.Header().Set("Content-Type", "test")
		// get header from response
		contentType := w.Header().Get("Content-Type")
		fmt.Println(contentType)
		w.WriteHeader(200)
	})

	server := http.Server{
		Addr: 	"localhost:5000",
		Handler: mux,
	}

	fmt.Println("Server running on", server.Addr)
	err := server.ListenAndServe()
	if err != nil {
		panic(err)
	}
}

```

<figure><img src="../.gitbook/assets/1 (3) (1).png" alt=""><figcaption></figcaption></figure>
