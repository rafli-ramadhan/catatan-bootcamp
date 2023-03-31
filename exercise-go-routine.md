# Exercise Go Routine

Check name in slice using go routine and context wait timeout.

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

var duration = 100*time.Millisecond
var wg = new(sync.WaitGroup)
var numberOfWorkers = 5
var start = time.Now()

func main() {
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

	fmt.Println("[CHANNEL] - Found", total, "of Wina. Done in", time.Since(start).Seconds(), "seconds")
	wg.Done()
}

func checkNameWithChannelAndWorker(ctx context.Context) {
	numOfBuffer := 5
	
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

		wg.Add(numberOfWorkers)

		var channelUserFound = make(chan string, numOfBuffer)
		go func() {
			fmt.Println("[CHANNEL+WORKER] - start check name")
			for workerIndex := 0; workerIndex < numberOfWorkers; workerIndex++ {
				var total int
				go func(workerIndex int) {
		
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
					fmt.Println("[CHANNEL+WORKER] - worker -", workerIndex+1, "found", total, "of Wina. Done in", duration.Seconds(), "seconds")

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
	}()

	select {
	case <-ctx.Done():
		fmt.Printf("[CHANNEL+WORKER] - finding stopped, %s\n", ctx.Err())
	}
}

func checkNameWithWorker(ctx context.Context, usernames []string) {
	wg.Add(numberOfWorkers)

	go func() {
		fmt.Println("[WORKER] - start check name")
		for workerIndex := 0; workerIndex < numberOfWorkers; workerIndex++ {
			var total int
			go func(workerIndex int) {
	
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
				fmt.Println("[WORKER] - worker -", workerIndex+1, "found", total, "of Wina. Done in", duration.Seconds(), "seconds")

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
[WORKER] - start wg wait
[CHANNEL] - start receive data from channel
[CHANNEL] - start send data to channel
[CHANNEL+WORKER] - start wg wait
[CHANNEL+WORKER] - start check name
[WORKER] - start check name
[CHANNEL+WORKER] - start send data to channel
[CHANNEL] - end send data to channel
[CHANNEL] - end receive data from channel
[CHANNEL] - Found 1 of Wina. Done in 0.0087968 seconds
[WORKER] - worker - 1 found 1 of Wina. Done in 0.00771 seconds
[WORKER] - worker - 5 found 1 of Wina. Done in 0.00771 seconds
[WORKER] - worker - 4 found 1 of Wina. Done in 0.00771 seconds
[WORKER] - worker - 3 found 1 of Wina. Done in 0.00771 seconds
[WORKER] - worker - 2 found 1 of Wina. Done in 0.00771 seconds
[CHANNEL+WORKER] - end send data to channel
[CHANNEL+WORKER] - worker - 1 found 0 of Wina. Done in 0.0138077 seconds
[WORKER] - end check name
[CHANNEL+WORKER] - worker - 3 found 0 of Wina. Done in 0.0138077 seconds
[CHANNEL+WORKER] - end check name
[CHANNEL+WORKER] - worker - 2 found 0 of Wina. Done in 0.0138077 seconds
[CHANNEL+WORKER] - worker - 5 found 1 of Wina. Done in 0.0138077 seconds
[CHANNEL+WORKER] - worker - 4 found 0 of Wina. Done in 0.0138077 seconds
[CHANNEL+WORKER] - end wg wait
```
