# Os

## Os.Create

Untuk create data di suatu file

```go
package main

import(
	"log"
	"os"
)

func main() {
	csvfile, err := os.Create("file/bookstore.csv")
	if err != nil {
		log.Panicln("Error create data", err)
	}

	defer func() {
		if err := csvfile.Close(); err != nil {
			log.Panicln("Error closing file", err)
		}
	}()
}
```

```
2023/04/10 11:22:11 Error create data open file/bookstore.csv: The system cannot find the path specified.
panic: Error create data open file/bookstore.csv: The system cannot find the path specified.
```
