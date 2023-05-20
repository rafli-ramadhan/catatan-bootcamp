# Request Method dan URI

Request merupakan informasi yang dikirim oleh client beberapa jenis request terdapat request method, request query parameter, request post form, request header get dan add yang akan di bahas di bawah ini.

## Request Method dan URI

Request ini digunakan untuk memperoleh method dan URL yang dikirim oleh client. Berikut adalah contoh _code_ untuk memperoleh request method dan URI.

```go
package main

import (
	"fmt"
	"net/http"
)

func main() {
	mux := http.NewServeMux()

	// request -> data type: struct
	var handlerMain http.HandlerFunc = func(w http.ResponseWriter, r *http.Request) {
		fmt.Println("Server running")
		fmt.Fprintf(w, "Server running")
		fmt.Fprintf(w, r.Method)
		fmt.Fprintf(w, r.RequestURI)
	}
	mux.HandleFunc("/main", handlerMain)

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
