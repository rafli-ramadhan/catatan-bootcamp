# Serve File

Kegunaan file server adalah untuk menampilkan suatu file yang ada dalam satu direktori yang sama dengan aplikasi.

```go
package main

import (
	"fmt"
	"net/http"
)

func main() {
	mux := http.NewServeMux()
	// menampilkan file melalui direktori (index.html utama)
	fs1 := http.FileServer(http.Dir("files/html"))
	fs2 := http.FileServer(http.Dir("files/txt"))
	mux.Handle("/", fs1)
	// jika didepan / ada tambahan kata, harus dihapus dengan http.StripPrefix
	mux.Handle("/html1", http.StripPrefix("/html2", fs1))
	mux.Handle("/txt", http.StripPrefix("/txt", fs2))

	// serve file digunakan untuk 
	mux.HandleFunc("/html2", func(w http.ResponseWriter, r *http.Request) {
		http.ServeFile(w, r, "./files/index.html")
	})
	mux.HandleFunc("/html3", func(w http.ResponseWriter, r *http.Request) {
		http.ServeFile(w, r, "./files/html/test1.html")
		// http.ServeFile(w, r, "./files/html/test2.html") // tidak akan ditampilkan
	})
	mux.HandleFunc("/txt2", func(w http.ResponseWriter, r *http.Request) {
		http.ServeFile(w, r, "./files/txt/test1.txt")
		// http.ServeFile(w, r, "./files/txt/test2.txt") // tidak akan ditampilkan
	})

	server := http.Server{
		Addr: 	"localhost:5000",
		Handler: mux,
	}

	fmt.Println("Server running on", server.Addr)
	err := server.ListenAndServe()
	if err != nil {
		panic(err)
	}
}
```

Struktur file dalam direktori ./file, ./file/html dan ./file/txt.

<figure><img src="../.gitbook/assets/folder file serve (1).png" alt=""><figcaption></figcaption></figure>
