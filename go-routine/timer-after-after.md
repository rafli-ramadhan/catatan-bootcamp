# Timer, After, After

## Timer

Timer adalah representasi waktu satu kejadian

Ketika waktu timer sudah expire, maka event akan dikirim ke dalam channel Untuk membuat Timer kita bisa menggunakan fungsi time.NewTimer(duration).

Fungsi time.NewTimer() mengembalikan struct \*time.Timer yang memiliki property C yang bertipe channel.

```go
package main
 
import (
    "fmt"
    "time"
)

func main() {
    timer := time.NewTimer(5 * time.Second)
    fmt.Println(time.Now())
    
    timeTimer := <-timer.C
    fmt.Println(timeTimer)
}
```

```
2023-03-28 11:25:07.7328437 +0700 +07 m=+0.002623201
2023-03-28 11:25:12.7468608 +0700 +07 m=+5.016640301
```

## After

Kadang kita hanya butuh channel nya saja, tidak membutuhkan data Timer nya Untuk melakukan hal itu kita bisa menggunakan function time.After(duration)

<pre class="language-go"><code class="lang-go">package main
 
import (
    "fmt"
    "time"
)

func main() {
    timer := time.After(1 * time.Second)
    fmt.Println(time.Now())
    
    timeTimer := &#x3C;-timer
<strong>    fmt.Println(timeTimer)
</strong>}
    
</code></pre>

```
2023-03-28 11:33:45.2167092 +0700 +07 m=+0.002684001
2023-03-28 11:33:46.2264751 +0700 +07 m=+1.012449901
```

## AfterFunc

AfterFunc -> untuk menjalankan sebuah function dengan delay waktu tertentu.

```go
package main
 
import (
    "fmt"
    "sync"
    "time"
)

func main() {
    wg := sync.WaitGroup{}
    wg.Add(1)
    time.AfterFunc(1*time.Second, func() {
        fmt.Println("execute after func")
        wg.Done()
    })

    fmt.Println("start")
    wg.Wait()
    fmt.Println("finish")
}
```

```
start
execute after func
finish
```
