# Rune & Byte

Rune -> Int32

Byte -> Uint8

String dibuat dari byte dan bisa direpresentasikan menggunakan rune.

Rune() bisa digunakan untuk convert string -> array rune.

Perbedaan rune dan byte -> karakter (string) non-ASCII pada byte saat di encode akan di ubah menjadi 2 byte.

```go
package main
 
import (
    "fmt"
)
 
func main() {
    s := "GÖLANG PROGRAMMING golang programming" // Ö is a non-ASCII character 
 
    s_rune := []rune(s)
    s_byte := []byte(s)
     
    fmt.Println(s_rune)
    fmt.Println(s_byte)
}
```

```
[71 214 76 65 78 71 32 80 82 79 71 82 65 77 77 73 78 71 32 103 111 108 97 110 103 32 112 114 111 103 114 97 109 109 105 110 103]
[71 195 150 76 65 78 71 32 80 82 79 71 82 65 77 77 73 78 71 32 103 111 108 97 110 103 32 112 114 111 103 114 97 109 109 105 110 103]
```

Reference :

[https://golangdocs.com/rune-in-golang](https://golangdocs.com/rune-in-golang)
