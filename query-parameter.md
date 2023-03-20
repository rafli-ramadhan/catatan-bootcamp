# Query Parameter

Query parameter -> data yang disimpan di URI

URL -> localhost:5000?name=andi\&age=21

Code -> request.URL.Query.Get()

```go
package main

import (
	"fmt"
	"net/http"
	"strconv"
)

func main() {
	mux := http.NewServeMux()

	var handlerMain http.HandlerFunc = func(write http.ResponseWriter, request *http.Request) {
		fmt.Printf("Server running")
		// fmt.Fprintf(write, request.Method)
		// fmt.Fprintf(write, request.RequestURI)

		name := request.URL.Query().Get("name")
		if name != "" {
			fmt.Fprintf(write, "Name : %s\n", name)
		} else {
			fmt.Fprintf(write, "Data in name query parameter is not exist\n")
		}

		age := request.URL.Query().Get("age")
		if age != "" {
			fmt.Fprintf(write, "Age : %s\n", &age)
		} else {
			fmt.Fprintf(write, "Data in age query parameter is not exist\n")
		}
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
