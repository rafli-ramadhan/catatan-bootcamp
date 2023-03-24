# Streaming Decoder & Encoder

Pada kenyataanya, kadang data JSON nya berasal dari Input berupa io.Reader (File, Network, Request Body) Kita bisa saja membaca semua datanya terlebih dahulu, lalu simpan di variable, baru lakukan konversi dari JSON, namun hal ini sebenarnya tidak perlu dilakukan, karena package json memiliki fitur untuk membaca data dari Stream.

Decoder -> JSON -> Go object

Encoder -> Go object -> JSON

## Decode JSON -> Struct

```go
package main

import (
    "encoding/json"
	"fmt"
	"os"
)

type Customer struct {
    Name string
    Age  int
}

func main() {
    customer := Customer{}

    reader, _ := os.Open("customer.json")
    decoder := json.NewDecoder(reader)
    decoder.Decode(&customer)
    fmt.Println(customer)
}
```

## Encode Struct -> JSON

```go
package main

import (
    "encoding/json"
    "fmt"
    "os"
)

type Customer struct {
    Name    string
    Age     int
    Married bool
}

func main() {
    customer := []Customer{
        {
            Name: "Andi",
            Age: 20,
            Married: false,
        },
        {
            Name: "Utsman",
            Age: 21,
            Married: true,
        },
    }

    writer, _ := os.Create("sample_output.json")
    encoder := json.NewEncoder(writer)
    encoder.Encode(customer)
    fmt.Println(customer)
}
```

```
[{Andi 20 false} {Utsman 21 true}]
```

JSON file "sample\_output.json" will be created with the contents

```
[{"Name":"Andi","Age":20,"Married":false},{"Name":"Utsman","Age":21,"Married":true}]
```

