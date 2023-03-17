# Slice

Kelebihan slice -> tidak perlu mendefinisikan berapa banyak value yang akan ditampung dalam data

Kekurangan slice -> saat diinputkan value yang melebihi capasitas slice, maka capasitas slice akan menjadi 2 kali lipat.

```go
package main

import (
	"fmt"
)

func main() {
	
	var names [3]string
	names[0] = "Test1"
	names[1] = "Test2"
	names[2] = "Test3"
	fmt.Printf("%s %s %s \n", names[0], names[1], names[2])

	var values = [3]int{12, 13, 14}
	fmt.Println(values)

	var strings = [3]string{"Test1", "Test2", "Test3"}
	fmt.Println(strings)

	var months = [12]string{"January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"}
	var newSlice1 = months[:]
	fmt.Printf(newSlice1[0])
	var newSlice2 = months[2:]
	fmt.Printf(newSlice2[0])
	var newSlice3 = months[:4]
	fmt.Printf(newSlice3[0])
	var newSlice4 = months[4:7]
	fmt.Printf(newSlice4[0])
	var newSlice5 = months[6:9]
	fmt.Printf(newSlice5[0])
	fmt.Printf("\n%v ", months)
	newSlice1[0] = "Indah"
	fmt.Printf("\n%v ", months)
	
	fmt.Printf(months[2])
	fmt.Printf(months[3])

	/*var names2 = [...]string("Test1", "Test2"}
	fmt.Printf(name2)

	newSlice := make([]string, 2, 5)
    newSlice[0] = "Umar"
	newSlice[1] = "Umar"
	fmt.Println(len(newSlice))
	fmt.Println(cap(newSlice))*/
}
```

