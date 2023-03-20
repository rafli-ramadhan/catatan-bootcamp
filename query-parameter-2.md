# Query Parameter 2

URL -> [http://localhost:5000/?name=andi\&age=21\&name=nuh\&age=22](http://localhost:5000/?name=andi\&age=21\&name=nuh\&age=22)

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
		fmt.Println("Server running")

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

Output in web browser :&#x20;

```
Data 1 : [andi nuh]
Data 2 : [21 22]
```
