# Query Parameter 2

Code -> request.URL.Query() -> Output -> map\[string]\[]string

```go
package main

import (
	"fmt"
	"net/http"
)

func main() {
	mux := http.NewServeMux()

	var handlerMain http.HandlerFunc = func(write http.ResponseWriter, request *http.Request) {
		fmt.Printf("Server running")

		urlValues := request.URL.Query()
		fmt.Fprintf(write, "Data 1 : %s\n", urlValues["name"])
		fmt.Fprintf(write, "Data 2 : %s\n", urlValues["age"])
	}
	mux.HandleFunc("/", handlerMain)

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
