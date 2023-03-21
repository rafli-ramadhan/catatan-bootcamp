# Query Parameter

Query parameter -> data yang disimpan di URI

Query parameter -> case sensitif -> huruf besar kecil berpengaruh

URL -> [http://localhost:5000/?name=andi\&age=21](http://localhost:5000/?name=andi\&age=21\&name=nuh\&age=22)&#x20;

```go
request.URL.Query.Get()
```

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

		name := request.URL.Query().Get("name")
		if name != "" {
			fmt.Fprintf(write, "Name : %s\n", name)
		} else {
			fmt.Fprintf(write, "Data in name query parameter is not exist\n")
		}

		age := request.URL.Query().Get("age")
		if age != "" {
			fmt.Fprintf(write, "Age : %s\n", age)
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

Output di web browser:

```
Name : andi
Age : 21
```
