# Context Parent and Child

Context bisa diterapkan parent dan chlid, 1 parent bisa punya banyak child, tapi 1 child hanya bisa punya 1 parent.

![](../.gitbook/assets/image.png)

Saat dilakukan pembatalan context A, maka semua child dan sub child dari context A akan ikut dibatalkan.

Jika kita membatalkan context B, hanya context B dan semua child dan sub child nya yang dibatalkan, context A tidak akan ikut dibatalkan.

Jika kita menyisipkan data ke dalam context A, semua child dan sub child nya bisa mendapatkan data tersebut.

jika kita menyisipkan data di context B, hanya context B dan semua child dan sub child nya yang mendapat data, context A tidak akan mendapat data.

Context -> object yang Immutable -> setelah Context dibuat, dia tidak bisa diubah lagi Ketika kita menambahkan value ke dalam context, atau menambahkan pengaturan timeout dan yang lainnya, secara otomatis akan membentuk child context baru, bukan merubah context tersebut.

Pada saat awal membuat context, context tidak memiliki value Kita bisa menambah sebuah value dengan data Pair (key - value) ke dalam context.

Saat kita menambah value ke context, secara otomatis akan tercipta child context baru -> original context nya tidak akan berubah sama sekali.

Untuk membuat menambahkan value ke context, kita bisa menggunakan function context.WithValue(parent, key, value)

```go
package main

import(
    "context"
    "fmt"
)

func main() {
    value := map[string]string{
        "1": "one",
        "2": "two",
    }
    background := context.Background()
    child := context.WithValue(background, "value", value)
    todo := context.TODO()

    fmt.Println(background)
    fmt.Println(child)
    fmt.Println(child.Value("value"))
    fmt.Println(todo)
}
```

```
context.Background
context.Background.WithValue(type string, val <not Stringer>)
map[1:one 2:two]
context.TODO
```
