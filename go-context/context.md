# Context

Context -> sebuah data yang membawa value, sinyal cancel, sinyal timeout dan sinyal deadline.

Context biasanya dibuat per request (misal setiap ada request masuk ke server web melalui http request).

Context digunakan untuk mempermudah kita meneruskan value, dan sinyal antar proses.

Context biasa digunakan untuk mengirim data request atau sinyal ke proses lain.

Dengan menggunakan context, ketika kita ingin membatalkan semua proses, kita cukup mengirim sinyal ke context, maka secara otomatis semua proses akan dibatalkan.

Context digunakan untuk -> database, http server, http client, dan lain-lain.

```go
type Context interface {
   Deadline() (deadline time.Time, ok bool)
    Done() <-chan struct{}
   Err() error
    Value(key interface{}) interface{}
}
```
