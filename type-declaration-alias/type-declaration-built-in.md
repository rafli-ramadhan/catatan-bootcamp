# Type Declaration Built In

Golang juga memiliki tipe data built in menggunakan type declaration sebagai berikut.

<figure><img src="../.gitbook/assets/alias.png" alt=""><figcaption><p>Tipe data built-in di Golang.</p></figcaption></figure>

## Rune dan Byte

Salah satu tipe data built in di Golang adalah rune dan byte. Perbedaan rune dan byte dapat diketahui dari konversi karakter non-ASCII (contohnya Ö) menjadi rune atau byte. Pada byte karakter non-ASCII saat di encode akan di ubah menjadi 2 byte, sementara di rune hanya menjadi 1 byte. Selain itu, byte juga digunakan untuk membuat string dan bisa direpresentasikan menggunakan rune.

## Contoh _code_

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
