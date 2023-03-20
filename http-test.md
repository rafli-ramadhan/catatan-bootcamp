# HTTP Test

HTTP Test -> NewRequest() & NewRecorder() -> untuk tes response dari suatu URL tanpa harus membuat server.

```go
package main

import (
	"fmt"
	"io"
	"net/http"
	"net/http/httptest"
)

func Test(write http.ResponseWriter, request *http.Request) {
	fmt.Println("Server running")
	fmt.Fprintln(write, "Success")
}

func main() {
	// server
	mux := http.NewServeMux()
	mux.HandleFunc("/test", Test)

	// request & response
	request := httptest.NewRequest("GET", "http://localhost:5000/test", nil)
	recorder := httptest.NewRecorder()

	Test(recorder, request)

	response := recorder.Result()
	body, _ := io.ReadAll(response.Body)

	fmt.Println(response)
	fmt.Println(response.StatusCode)
	fmt.Println(response.Status)
	fmt.Println(string(body))
}
```

```
Server running
&{200 OK 200 HTTP/1.1 1 1 map[Content-Type:[text/plain; charset=utf-8]] {0xc000071080} -1 [] false false map[] <nil> <nil>}
200
200 OK
Success
```



