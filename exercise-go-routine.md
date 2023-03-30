# Exercise Go Routine

```go
package main

import (
	"fmt"
	"log"
	"strings"
	"sync"
	"time"
)

var usernames []string = []string{
	"Aditya Ananta Putra",
	"ADNAN NUR JAILANI",
	"Afrila Zahra Prasetyo",
	"Aida Nirmala",
	"Amalia Rahma",
	"ANDINI DWI RIZKY PUTRI",
	"Angga Putra",
	"CAHAYA WIJAYA IJAM",
	"Dea Christina",
	"DEVITA NANDA OKTAVIA",
	"DEWI AYU LESTARI",
	"Dhevina Ananda Fitri",
	"DHEVY YANI RIZKI",
	"Dwi Mahani",
	"Eri Santosos",
	"Faiza Amalia Mahfudz",
	"FAUZIYATUNNISA",
	"Febriyanti Syabina",
	"Hafifah Nur Azmi Pratiwi",
	"Juliansyah Husien",
	"Kharisa Nur Aziza",
	"Lun Wina",
	"MAHREVA ROESTHA RAMADANIATY",
	"MUHAMMAD FADHILAH",
	"Muhammad Fatah Firdaus",
	"Muhammad Rafly Ahya",
	"Muhammad Rahmin Noor",
	"Muhammad Rivaldi",
	"Muhammad Rizky Rachmadhani",
	"Nadiah Nahdhah Islamiyah",
	"NOLA FEBRIANA SAPUTRI",
	"RAFADYAN REYHAN MARITZA WERAT",
	"Robby Satria",
	"Salshabilla Wahyu Anafi",
	"STEVI VIONI PAKULLA",
	"Winny Rahmah Nia",
}

var wg sync.WaitGroup

func check(usernames ...string) (totalData int, checkName []string, totalAperData map[string]int) {
	totalAperData = map[string]int{}
	for _, username := range usernames {
		wg.Add(1)
		go func(username string) {
			defer wg.Done()
			// check if username contain alphabet "A"
			if strings.Contains(strings.ToLower(username), "wina") {
				checkName = append(checkName, username)
			}

			// calculate total data
			totalData++

			// calculate "A" for every data
			totalA := 0
			for j := range username {
				if strings.ToLower(string(username[j])) == "a" {
					totalA += 1
				}
			}
			totalAperData[username] = totalA
		}(username)

		wg.Wait()
	}

	return totalData, checkName, totalAperData
}

func main() {
	log.Println("start")
	start := time.Now()
	fmt.Println()

	totalData, checkName, totalAperData := check(usernames...)

	fmt.Println(totalData)
	fmt.Println()
	fmt.Println(checkName)
	fmt.Println()
	fmt.Println(totalAperData)
	
	fmt.Println()
	duration := time.Since(start)
	log.Println("Done in", duration.Seconds(), "seconds")
}
```

```
2023/03/30 15:16:28 start

36

[Lun Wina]

map[ADNAN NUR JAILANI:4 ANDINI DWI RIZKY PUTRI:1 Aditya Ananta Putra:6 Afrila Zahra Prasetyo:5 Aida Nirmala:4 Amalia Rahma:5 Angga Putra:3 CAHAYA WIJAYA IJAM:6 DEVITA NANDA OKTAVIA:5 DEWI AYU LESTARI:2 DHEVY YANI RIZKI:1 Dea Christina:2 Dhevina Ananda Fitri:4 Dwi Mahani:2 Eri Santosos:1 FAUZIYATUNNISA:3 Faiza Amalia Mahfudz:6 Febriyanti Syabina:3 Hafifah Nur Azmi Pratiwi:4 Juliansyah Husien:2 Kharisa Nur Aziza:4 Lun Wina:1 MAHREVA ROESTHA RAMADANIATY:7 MUHAMMAD FADHILAH:4 Muhammad Fatah Firdaus:5 Muhammad Rafly Ahya:5 Muhammad Rahmin Noor:3 Muhammad Rivaldi:3 Muhammad Rizky Rachmadhani:5 NOLA FEBRIANA SAPUTRI:4 Nadiah Nahdhah Islamiyah:6 RAFADYAN REYHAN MARITZA WERAT:7 Robby Satria:2 STEVI VIONI PAKULLA:2 Salshabilla Wahyu Anafi:6 Winny Rahmah Nia:3]

2023/03/30 15:16:28 Done in 0.0016152 seconds
```
