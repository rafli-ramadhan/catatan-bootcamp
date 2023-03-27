# Request Query Parameter -> r.URL.Query.Get()

Query parameter -> data yang disimpan di URI

Query parameter -> case sensitif -> huruf besar kecil berpengaruh

```go
r.URL.Query().Get()
```

```go
r.URL.Query() // Output -> map[string][]string
```

URL -> [http://localhost:5000/?name=andi\&age=21](http://localhost:5000/?name=andi\&age=21\&name=nuh\&age=22)&#x20;

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

URL -> [http://localhost:5000/?name=andi\&age=21\&name=nuh\&age=22](http://localhost:5000/?name=andi\&age=21\&name=nuh\&age=22)

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

Output in web browser :

```
Data 1 : [andi nuh]
Data 2 : [21 22]
```
