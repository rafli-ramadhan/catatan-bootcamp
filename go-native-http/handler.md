# Handler

Handler merupakan program yang berguna untuk menerima request dari client dan memberikan response ke client. Dalam package http mux terdapat 2 jenis handler yaitu http.Handle() dan http.HandleFunc(). HTTP **handle** menerima input handler dengan tipe **Handler**. Sementara HTTP **handleFunc** menerima input handler dengan tipe **HandlerFunc**.

Handler merupakan **interface**. Artinya semua variabel yang punya method ServeHTTP dapat dikatakan sama dengan Handler.&#x20;

HandlerFunc merupakan variabel dengan tipe data func(ResponseWriter. \*Request). Artinya semua fungsi yang memiliki input ResponseWriter dan \*Request dapat dikatan sama dengan HandlerFunc. HandlerFunc dalam package http memiliki method ServeHTTP. Artinya HandlerFunc juga mirip seperti Handler.&#x20;

Perbedaannya, suatu variabel dengan tipe Handle harus didefinisikan dengan method ServeHTTP, sementara variabel dengan tipe HandlerFunc tidak harus.&#x20;

```go
type Handler interface {
	ServeHTTP(ResponseWriter, *Request)
}
```

```go
type HandlerFunc func(ResponseWriter, *Request)

// ServeHTTP calls f(w, r).
func (f HandlerFunc) ServeHTTP(w ResponseWriter, r *Request) {
	f(w, r)
}

```

Pola _code_ di atas mirip dengan _code_ dibawah ini.

```go
package main

import (
	"fmt"
)

func main() {
	// deklarasi variabel b dengan tipe A
	var b A
	b = func(i1 int, i2 int) {
		fmt.Println(i1 + i2)
	}
	// panggil method Test
	b.Test(2, 2)
}

type A func(int, int)

func (a A) Test(i1 int, i2 int) {
	a(i1, i2)
}

```

```
4
```

## Contoh handler dengan http handle

Jika kita menggunakan http.Handle() maka harus membuat variabel yang punya method ServeHTTP terlebih dahulu seperti contoh _code_ di bawah ini.

```go
package main

import (
    "fmt"
    "net/http"
)

type HelloHandler struct{}

func (h *HelloHandler) ServeHTTP(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Hello!")
}

type WorldHandler struct{}

func (h *WorldHandler) ServeHTTP(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "World!")
}
func main() {
    hello := HelloHandler{}
    world := WorldHandler{}
    http.Handle("/hello", &hello)
    http.Handle("/world", &world)
    http.ListenAndServe(":8080", nil)
}
```

## Contoh _code_ dengan HTTP handle func.

Jika kita menggunakan http.HandleFunc() tidak perlu membuat method ServeHTTP untuk handler karena sudah ada dalam package http.

```go
package main

import (
    "fmt"
    "net/http"
)

// handler
func hello(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Hello!")
}

func world(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "World!")
}

func main() {
    http.HandleFunc("/hello", hello)
    http.HandleFunc("/world", world)
    http.ListenAndServe(":8080", nil)
}
```

Referensi:

{% embed url="https://stackoverflow.com/questions/21957455/difference-between-http-handle-and-http-handlefunc" %}
