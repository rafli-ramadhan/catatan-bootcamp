# Write Header

Untuk menambahkan header di response dapat menggunakan

```go
write.Header().Add("Content-Type", "application/json")
```

```go
package main

import (
	"fmt"
	"io"
	"net/http"
	"net/http/httptest"
)

func RequestHeader(write http.ResponseWriter, request *http.Request) {
	request.Header.Add("Content-Type", "application/json")

	write.Header().Add("Content-Type", "application/json")
	write.Header().Add("Content-Type", "application/json")
	write.Header().Add("X-Powered-By", "Phincon")
	
	request.Header.Get("Content-Type")
}

func ResponseHeader(write http.ResponseWriter, request *http.Request) {
}

func NotFound(write http.ResponseWriter, request *http.Request) {
	w.WriteHeader(404)
}

func main() {
	// server
	mux := http.NewServeMux()
	mux.HandleFunc("/test", RequestHeader)
	mux.HandleFunc("/not-found", NotFound

	// httptest
	request := httptest.NewRequest("GET", "http://localhost:5000/test", nil)
	recorder := httptest.NewRecorder()
	RequestHeader(recorder, request)

	response := recorder.Result()
	body, _ := io.ReadAll(response.Body)

	fmt.Println(response)
	fmt.Println(response.Header.Get("Content-Type"))
	fmt.Println(response.Header.Get("X-Powered-By"))
	fmt.Println(string(body2))
}
```

```
&{200 OK 200 HTTP/1.1 1 1 map[Content-Type:[application/json]] {0xc000071080} -1 [] false false map[] <nil> <nil>}
application/json

&{200 OK 200 HTTP/1.1 1 1 map[Content-Type:[application/json] X-Powered-By:[Phincon]] {0xc0000711d0} -1 [] false false map[] <nil> <nil>}
Phincon
```
