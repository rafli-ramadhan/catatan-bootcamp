# Request Post Form -> r.PostForm.Get()

Saat kita belajar HTML, kita tahu bahwa saat kita membuat form, kita bisa submit datanya dengan method GET atau POST.

Jika menggunakan method GET -> semua data di form akan menjadi query parameter.

Sedangkan jika menggunakan POST -> semua data di form akan dikirim via body HTTP request.

ParseForm mengambil (parses) query mentah dari URL seperti dari CURL and melakukan update r.PostForm

```go
r.PostForm.Get()
```

```go
package main

import (
	"fmt"
	"io"
	"net/http"
	"net/http/httptest"
	"strings"
)

func FormPost(write http.ResponseWriter, request *http.Request) {
	err := request.ParseForm()
	if err != nil {
		panic(err)
	}

	firstName := request.PostForm.Get("first_name")
	lastName := request.PostForm.Get("last_name")
	age := request.PostForm.Get("age")
	
	fmt.Fprintf(write, "Hello %s %s and I am %s years old", firstName, lastName, age)
}

func main() {
	requestBody := strings.NewReader("first_name=Utsman&last_name=Bey&age=23")
	request := httptest.NewRequest(http.MethodPost, "localhost:5000/", requestBody)
	request.Header.Add("Content-Type", "application/x-www-form-urlencoded")
	recorder := httptest.NewRecorder()
	FormPost(recorder, request)
	response := recorder.Result()
	body, _ := io.ReadAll(response.Body)
	fmt.Println(string(body))
}
```

```
Hello Utsman Bey and I am 23 years old
```
