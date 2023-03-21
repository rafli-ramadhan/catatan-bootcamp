# Get and Set Cookie

Cookie merupakan data yang dibuat di server dan dikirimkan ke web browser dan sengaja agar disimpan di web browser.

Penerapan -> untuk menyimpan data token saat user login.

```go
package main

import (
	"fmt"
	"net/http"
)

func RequestHeader(write http.ResponseWriter, request *http.Request) {
	fmt.Println("Server running")
	fmt.Fprintln(write, "Server running")
}

func SetCookie(write http.ResponseWriter, request *http.Request) {
	cookie := new(http.Cookie)
	cookie.Name = "X-Powered-By"
	cookie.Value = request.URL.Query().Get("name")
	cookie.Path = "/set-cookie"
	http.SetCookie(write, cookie)
	fmt.Fprintln(write, "Success create cookie")
}

func GetCookie(write http.ResponseWriter, request *http.Request) {
	cookie, err := request.Cookie("X-Powered-By")
	if err != nil {
		fmt.Fprint(write, "No Cookie")
	} else {
		fmt.Fprintf(write, "Cookie value : %s", cookie.Value)
	}
}	

func main() {
	// server
	mux := http.NewServeMux()
	mux.HandleFunc("/", RequestHeader)
	mux.HandleFunc("/set-cookie", SetCookie)
	mux.HandleFunc("/get-cookie", GetCookie)

	server := http.Server{
		Addr: "localhost:5000",
		Handler: mux,
	}

	err := server.ListenAndServe()
	if err != nil {
		panic(err.Error())
	}
	fmt.Println("Server running")
}
```

Output showed in [http://localhost:5000/set-cookie](http://localhost:5000/get-cookie)

```
Success create cookie
```

Output showed in [http://localhost:5000/get-cookie](http://localhost:5000/get-cookie)

```
Cookie value : 
```

