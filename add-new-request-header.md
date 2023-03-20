# Add New Request Header

Untuk menambahkan request header baru

```go
request.Header.Add()
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
	contentType := request.Header.Get("content-type")
	fmt.Fprintln(write, contentType)
}

func main() {
	// server
	mux := http.NewServeMux()
	mux.HandleFunc("/test", RequestHeader)

	// request & response
	request := httptest.NewRequest("GET", "http://localhost:5000/test", nil)
	request.Header.Add("Content-Type", "application/json")
	recorder := httptest.NewRecorder()

	RequestHeader(recorder, request)
	
	response := recorder.Result()
	body, _ := io.ReadAll(response.Body)

	fmt.Println(response)
	fmt.Println(response.StatusCode)
	fmt.Println(response.Status)
	fmt.Println(string(body))
}
```

```
&{200 OK 200 HTTP/1.1 1 1 map[Content-Type:[text/plain; charset=utf-8]] {0xc0000710b0} -1 [] false false map[] <nil> <nil>}
200
200 OK
application/json
```
