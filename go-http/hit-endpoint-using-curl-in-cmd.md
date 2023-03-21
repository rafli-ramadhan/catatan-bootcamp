# Hit Endpoint using Curl in CMD

## HTTP Get Method, Example :

```bash
curl -X GET http://localhost:5000
```

## HTTP Post Method, Example :

```bash
curl -X POST -d "first_name=Umar&last_name=Bawazir&age=20" http://localhost:5000/post
Hello Umar Bawazir. Iam 20 years old.
```

## Example Code

```go
package main

import (
	"fmt"
	"net/http"
)

func HandlerGet(write http.ResponseWriter, request *http.Request) {
	fmt.Println("Success", http.StatusOK)
	fmt.Println("Success")
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
	fmt.Println("Success", http.StatusOK)
	fmt.Printf("Hello %s %s and I am %s years old", firstName, lastName, age)
	fmt.Fprintf(write, "Hello %s %s and I am %s years old", firstName, lastName, age)
}

func main() {
	mux := http.NewServeMux()
	mux.HandleFunc("/", HandlerGet)
	mux.HandleFunc("/t", HandlerFormPost)

	server := http.Server{
		Addr:   "localhost:5000",
		Handler: mux,
	}

	err := server.ListenAndServe()
	if err != nil{
		panic(err.Error())
	}

	fmt.Println("Server running")
}
```

Run go run . in CMD 2 then open CMD 1 to do request.

## HTTP Get Method

CMD 1 (Request)

```bash
D:\go-server>curl -X GET http://localhost:5000
Success
```

CMD 2 (Response)

```bash
D:\go-server>go run .
Success
```

## HTTP Post Method

CMD 1 (Request)

```bash
D:\go-server>curl -X POST -d "first_name=Utsman,last_name=Bey,age=20" http://localhost:5000/t
Hello Utsman,last_name=Bey,age=20  and I am  years old
```

CMD 1 (Response)

```
D:\go-server>go run .
Hello Utsman,last_name=Bey,age=20  and I am  years old
```

## Reference

{% embed url="https://superuser.com/questions/149329/how-do-i-make-a-post-request-using-curl" %}
