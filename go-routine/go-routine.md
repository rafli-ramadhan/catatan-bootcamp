# Go Routine

**Go routine** -> thread ringan yang dikelola oleh go runtime -> untuk menjalakan concurrency di golang -> sifatnya asynchronous -> tidak saling tunggu -> dan secara random.

Go routine dijalankan oleh Go Scheduler dalam thread -> jumlah thread nya sebanyak GOMAXPROCS (biasanya sejumlah core CPU).

**Kelebihan** -> Go routine sangat ringan -> ukurannya hanya 2 kB.

**Parallel programming** -> memecahkan suatu blok kode dengan cara membaginya menjadi yang lebih kecil, dan dijalankan secara bersamaan pada waktu yang bersamaan pula.

{% embed url="https://miro.medium.com/v2/resize:fit:1400/1*ylONk4ex9q6IK68C6USRBg.jpeg" %}
[https://miro.medium.com/v2/resize:fit:1400/1\*ylONk4ex9q6IK68C6USRBg.jpeg](https://miro.medium.com/v2/resize:fit:1400/1\*ylONk4ex9q6IK68C6USRBg.jpeg)
{% endembed %}

```go
package main

import (
    "fmt"
    "time"
)

func numbers() {
    for i := 1; i <= 5; i++ {
        time.Sleep(250*time.Millisecond)
        fmt.Printf("%d ", i)
    }
}

func alphabets() {  
    for i := 'a'; i <= 'e'; i++ {
        time.Sleep(400*time.Millisecond)
        fmt.Printf("%c ", i)
    }
}

func text(num int, message string) {
    for i := 0; i < num; i++ {
        fmt.Printf("%s ", message)
    }
}

func main() {
    go numbers()
    go alphabets()
    go text(5, "halo")
    go text(5, "hai")
    text(5, "apa kabar")
    time.Sleep(3000*time.Millisecond)
    fmt.Println("end")
}
```

```
apa kabar apa kabar apa kabar apa kabar apa kabar hai hai hai hai hai halo halo halo halo halo 1 a 2 3 b 4 c 5 d e end
```
