# File Server

Go-Lang memiliki sebuah fitur yang bernama FileServer&#x20;

Kegunaan -> untuk membuat Handler di Go-Lang web yang digunakan sebagai static file server -> Dengan menggunakan FileServer, kita tidak perlu manual me-load file lagi FileServer adalah Handler, yang bisa ditambahkan ke http.Server atau http.ServeMux

```go
package main

import (
	"embed"
	"fmt"
	"net/http"
)

func HandlerGet(write http.ResponseWriter, request *http.Request) {
	write.WriteHeader(http.StatusOK)
	fmt.Println("Success", http.StatusOK)
	fmt.Fprintf(write, "Success")
}

func HandlerFormPost(write http.ResponseWriter, request *http.Request) {
	err := request.ParseForm()
	if err != nil {
		panic(err)
	}

	firstName := request.PostForm.Get("first_name")
	lastName := request.PostForm.Get("last_name")
	age := request.PostForm.Get("age")

	write.WriteHeader(http.StatusCreated)
	fmt.Println("Success", http.StatusCreated)
	fmt.Printf("Hello %s %s. Iam %s years old.\n", firstName, lastName, age)
	fmt.Fprintf(write, "Hello %s %s. Iam %s years old.\n", firstName, lastName, age)
}

//go:embed asset
var asset embed.FS
//go:embed resources
var resouces embed.FS

func main() {
	fileServer1 := http.FileServer(http.Dir("asset"))
	fileServer2 := http.FileServer(http.Dir("static"))
	fileServer3 := http.FileServer(http.FS(asset))
	fileServer4 := http.FileServer(http.FS(resouces))

	mux := http.NewServeMux()
	mux.HandleFunc("/get", HandlerGet)
	mux.HandleFunc("/post", HandlerFormPost)
	mux.Handle("/static-1/", http.StripPrefix("/static-1", fileServer1))
	mux.Handle("/static-2/", http.StripPrefix("/static-2", fileServer2))
	mux.Handle("/static-3/", http.StripPrefix("/static-3", fileServer3))
	mux.Handle("/static-4/", http.StripPrefix("/static-4", fileServer4))

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
