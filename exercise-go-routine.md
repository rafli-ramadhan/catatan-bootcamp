# Exercise Go Routine

```go
package main

import (
	"context"
	"fmt"
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

var wg = new(sync.WaitGroup)
	
func main() {	
	duration := 5000*time.Millisecond
	ctx, cancel := context.WithTimeout(context.Background(), duration)
	defer cancel()
	
	wg.Add(3)

	go func() {
		checkNameWithWorker(ctx, usernames)
		defer wg.Done()
	}()

	go func() {
		checkNameWithChannel()
		defer wg.Done()
	}()

	go func() {
		checkNameWithChannelAndWorker(ctx)
		defer wg.Done()
	}()

	wg.Wait()
}

func checkNameWithChannel() {
	numOfBuffer := 5
	var ch = make(chan string, numOfBuffer)
	start := time.Now()

	go func() {
		fmt.Println("[CHANNEL] - start send data to channel")
		for _, username := range usernames {
			ch <- username
		}
		fmt.Println("[CHANNEL] - end send data to channel")
		close(ch)
	}()
		
	var total int
	fmt.Println("[CHANNEL] - start receive data from channel")
	for i := range ch {
		if strings.Contains(strings.ToLower(i), "wina") {
			total++
		}
	}
	fmt.Println("[CHANNEL] - end receive data from channel")

	duration := time.Since(start)
	fmt.Println("[CHANNEL] - found", total, "of Wina. Done in", duration.Seconds(), "seconds")
	defer wg.Done()
}

func checkNameWithChannelAndWorker(ctx context.Context) {
	numOfBuffer := 5
	done := make(chan int)

	go func() {	
		var channelUser = make(chan string, numOfBuffer)
		go func() {
			fmt.Println("[CHANNEL+WORKER] - start send data to channel")
			for _, username := range usernames {
				select{
				case <-ctx.Done():
					break
				default:
					channelUser <- username
				}
			}
			fmt.Println("[CHANNEL+WORKER] - end send data to channel")
			close(channelUser)
		}()

		numberOfWorkers := 10
		wg.Add(numberOfWorkers)

		var channelUserFound = make(chan string, numOfBuffer)
		go func() {
			fmt.Println("[CHANNEL+WORKER] - start check name")
			for workerIndex := 0; workerIndex < numberOfWorkers; workerIndex++ {
				var total int
				go func(workerIndex int) {
					start := time.Now()
		
					for username := range channelUser {
						select {
						case <-ctx.Done():
							break
						default:
							if strings.Contains(strings.ToLower(username), "wina") {
								channelUserFound <- username
								total++
							}
						}
					}
					
					duration := time.Since(start)
					fmt.Println("[CHANNEL+WORKER] -", workerIndex+1, "found", total, "of Wina. Done in", duration.Seconds(), "seconds")

					wg.Done()
				}(workerIndex)
			}
			fmt.Println("[CHANNEL+WORKER] - end check name")
		}()

		go func() {
			fmt.Println("[CHANNEL+WORKER] - start wg wait")
			wg.Wait()
			fmt.Println("[CHANNEL+WORKER] - end wg wait")
		}()

		counterSuccess := 0
		listOfUser := []string{}
		for ch := range channelUserFound {
			counterSuccess++
			listOfUser = append(listOfUser, ch)
		}
		done <- counterSuccess
	}()

	select {
	case <-ctx.Done():
		fmt.Println("[CHANNEL+WORKER] - finding stopped, %s", ctx.Err())
	case counterTotal := <-done:
		fmt.Printf("[CHANNEL+WORKER] - %d of total found", counterTotal)
	}
}

func checkNameWithWorker(ctx context.Context, usernames []string) {
	numberOfWorkers := 10
	wg.Add(numberOfWorkers)

	go func() {
		fmt.Println("[WORKER] - start check name")
		for workerIndex := 0; workerIndex < numberOfWorkers; workerIndex++ {
			var total int
			go func(workerIndex int) {
				start := time.Now()
	
				for _, username := range usernames {
					select {
					case <-ctx.Done():
						break
					default:
						if strings.Contains(strings.ToLower(username), "wina") {
							total++
						}
					}
				}
				
				duration := time.Since(start)
				fmt.Println("[WORKER] -", workerIndex+1, "found", total, "of Wina. Done in", duration.Seconds(), "seconds")

				wg.Done()
			}(workerIndex)
		}
		fmt.Println("[WORKER] - end check name")
	}()

	go func() {
		fmt.Println("[WORKER] - start wg wait")
		wg.Wait()
		fmt.Println("[WORKER] - end wg wait")
	}()
}
```

```
2023/03/30 15:16:28 start

36

[Lun Wina]

map[ADNAN NUR JAILANI:4 ANDINI DWI RIZKY PUTRI:1 Aditya Ananta Putra:6 Afrila Zahra Prasetyo:5 Aida Nirmala:4 Amalia Rahma:5 Angga Putra:3 CAHAYA WIJAYA IJAM:6 DEVITA NANDA OKTAVIA:5 DEWI AYU LESTARI:2 DHEVY YANI RIZKI:1 Dea Christina:2 Dhevina Ananda Fitri:4 Dwi Mahani:2 Eri Santosos:1 FAUZIYATUNNISA:3 Faiza Amalia Mahfudz:6 Febriyanti Syabina:3 Hafifah Nur Azmi Pratiwi:4 Juliansyah Husien:2 Kharisa Nur Aziza:4 Lun Wina:1 MAHREVA ROESTHA RAMADANIATY:7 MUHAMMAD FADHILAH:4 Muhammad Fatah Firdaus:5 Muhammad Rafly Ahya:5 Muhammad Rahmin Noor:3 Muhammad Rivaldi:3 Muhammad Rizky Rachmadhani:5 NOLA FEBRIANA SAPUTRI:4 Nadiah Nahdhah Islamiyah:6 RAFADYAN REYHAN MARITZA WERAT:7 Robby Satria:2 STEVI VIONI PAKULLA:2 Salshabilla Wahyu Anafi:6 Winny Rahmah Nia:3]

2023/03/30 15:16:28 Done in 0.0016152 seconds
```
