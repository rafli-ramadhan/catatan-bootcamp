# Variable vs Constant

Variabel dan constant di golang sama-sama dapat di inisiasi suatu value dengan tipe data tertentu. Bedanya, nilai dari suatu constant tidak bisa diubah saat sudah di inisiasi suatu value.

## Contoh _code_

```go
package main

import "fmt"

func main() {
    var num1 int = 2
    fmt.Println(num1)

    // num1 di inisiasi dengan value berbeda
    num1 = 3
    fmt.Println(num1)
    
    const num2 int = 2
    fmt.Println(num2)

    // num2 di inisiasi dengan velue berbeda akan memunculkan error :
    // cannot assign to num2 (constant 2 of type int)
}
```

```
// Output
2
3
2
```
