# Map

Map di Golang memiliki pola seperti array atau slice yang menyimpan beberapa data dengan tipe data yang sama dengan key value yang bisa di custom. Sebelum digunakan, map perlu di inisiasi sebagai berikut.

```go
var example map[string]int = map[string]int{}
```

atau bisa menggunakan fungsi make() sebagai berikut.

```go
var example map[string]int = make(map[string]int)
```

## Contoh _code_

1. Buatlah map dengan key nama orang dan valuenya macam-macam hobi maksimal 3, dengan ketentuan berikut:&#x20;

a. Buat map dengan function make&#x20;

b. Isi map dengan 10 data&#x20;

c. Cetak dengan fungsi printf. Ex: “nama saya umar mempunya hobi gaming, hiking, dan fishing”

```go
package main

import (
	"fmt"
)

func main() {
    type hobbies []string
    
    var users map[string]hobbies = make(map[string]hobbies)
    users["Adni"]   = []string{"Golf"}
    users["Faras"]  = []string{"Basketball", "Diving", "Gold"}
    users["Dawam"]  = []string{"Diving", "Scating"}
    users["Rizky"]  = []string{"Golf"}
    users["Alfi"]   = []string{"Basketball", "Diving", "Gold"}
    users["Jason"]  = []string{"Diving"}
    users["Mega"]   = []string{"Golf", "Scating"}
    users["Albert"] = []string{"Basketball", "Diving", "Gold"}
    users["Fajar"]  = []string{"Diving"}
    users["Dito"]   = []string{"Golf"}
    
    for i := range users {
        var hobi string
        if len(users[i]) == 1 {
            hobi = fmt.Sprintf("%s", users[i][0])
        } else if len(users[i]) == 2 {
            hobi = fmt.Sprintf("%s dan %s", users[i][0], users[i][1])
        } else if len(users[i]) == 3 {
            hobi = fmt.Sprintf("%s, %s, dan %s", users[i][0], users[i][1], users[i][2])
        }
    
        fmt.Printf("\nNama saya %s mempunyai hobi %s", i, hobi)
    }
}
```

```
Nama saya Jason mempunyai hobi Diving
Nama saya Albert mempunyai hobi Basketball, Diving, dan Gold
Nama saya Dito mempunyai hobi Golf
Nama saya Adni mempunyai hobi Golf
Nama saya Faras mempunyai hobi Basketball, Diving, dan Gold
Nama saya Alfi mempunyai hobi Basketball, Diving, dan Gold
Nama saya Fajar mempunyai hobi Diving
Nama saya Dawam mempunyai hobi Diving dan Scating
Nama saya Rizky mempunyai hobi Golf
Nama saya Mega mempunyai hobi Golf dan Scating
```

## Contoh _code_ map string interface

Map string interface bisa digunakan untuk menampung key dengan tipe data string dan value dengan tipe data apapun. Map jenis ini sangat berguna untuk membuat REST API.

```go
package main
import "fmt"

func main() {
    var someMap map[string]interface{}
    
    someMap = map[string]interface{}{
        "username"  : "test",
        "age"       : 20,
    }
    
    fmt.Println(someMap)
}
```

```
map[age:20 username:test]
```

## Contoh _code_ map string dengan value map string interface

Map juga bisa diisi dengan value yang juga merupakan map seperti _code_ di bawah ini.

```go
package main
import "fmt"

func main() {
    var someMap map[string]map[string]interface{}
    var someSubMap map[string]interface{} = map[string]interface{}{
        "username"  : "dana",
        "age"       : 24,
    }

    someMap = map[string]map[string]interface{}{
        "map1"  : someSubMap,
        "map2"  : someSubMap,
    }
    
    fmt.Println(someMap["map1"])
    fmt.Println(someMap["map2"])
    fmt.Println(someMap["map1"]["username"])
}
```

```
map[age:24 username:dana]
map[age:24 username:dana]
dana
```
