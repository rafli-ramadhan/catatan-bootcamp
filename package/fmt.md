# Fmt

fmt.Println -> bisa untuk print tipe data int, float, bool, string, arr, map, slice dan struct.

fmt.Printf -> hanya untuk print formatting string

fmt.Sprintf -> untuk membuat variabel string dengan variabel dinamis

fmt.FPrintf atau fmt.Fprintln -> untuk menampilkan value ke sisi client

fmt.Scanln -> untuk memperoleh input dari sisi server -> tapi input tidak boleh dipisahkan oleh spasi.

## Printf vs Sprintf

```go
package main
  
import (
    "error"
    "fmt"
)

func main() {
    // a := fmt.Printf("Test %d", 123) // ssignment mismatch: 1 variable but fmt.Printf returns 2 values

    b := fmt.Sprintf("Test %d", 123)
    fmt.Println(b)
    
    err = errors.New("test error")
    if err != nil {
        log.Print(fmt.Sprintf("error : %s", err))
    }
}
```
