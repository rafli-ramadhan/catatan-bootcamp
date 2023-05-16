# Request Header Get

Untuk menangkap request header yang dikirim oleh client, kita bisa mengambilnya di Request.

Header mirip seperti Query Parameter -> isinya adalah map\[string]\[]string -> Berbeda dengan Query Parameter yang case sensitive, secara spesifikasi, Header key tidaklah case sensitive

Untuk mendapatkan header dari sisi client

```go
request.Header.Get("Content-Type")
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
		fmt.Println("Server running")

		headerAccept := request.Header.Get("Accept")
		fmt.Fprintf(write, "Header accept data : %s\n", headerAccept)

		headerHost := request.Header.Get("Host")
		fmt.Fprintf(write, "Header host data : %s\n", headerHost)
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

Output in web browser&#x20;

```
Header accept data : text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Header host data : 
```

