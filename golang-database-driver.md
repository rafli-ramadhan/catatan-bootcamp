# Golang Database Driver

Golang memiliki beberapa driver untuk koneksi database, diantarnya :

### 1. MySQL

Untuk instalasi dan set up bisa klik link berikut.

{% embed url="https://github.com/go-sql-driver/mysql" %}

### 2. PostgreSQL

Untuk instalasi dan set up bisa klik link berikut.

{% embed url="https://github.com/jackc/pgx" %}

## Golang Database Pool

Database pool digunakan untuk management access database di Golang. Di package "database/sql", Golang menyediakan 4 parameter management access seperti berikut.

```go
// database pool -> managemen koneksi
// setMaxIdelConns -> pengaturan jumlah koneksi minimal yang dibuat saat aplikasi connect ke database
// setMaxOpenConns -> pengaturan jumlah koneksi maksimal dibuat
// setConnMaxIdleTime -> contoh ada 10 koneksi tidak digunakan selamat durasi waktu tertentu, maka akan di close
// setConnMaxLifeTime -> contoh koneksi sudah mencapai waktu tertentu, maka akan di close atau memperbaruhi koneksi yang lama

db.SetMaxIdleConns(10)
db.SetMaxOpenConns(50)
db.SetConnMaxIdleTime(5 * time.Minute)
db.SetConnMaxLifetime(60 * time.Minute)
```

Jika SetMaxIdleConns dan SetMaxOpenCons diinisiasi value-nya, koneksi perlu segera mungkin di close setelah menjalankan query di suatu function di aplikasi Golang agar bisa digunakan untuk menjalankan query di function lain di satu aplikasi yang sama. Untuk close dapat menggunakan fungsi Close.

```go
defer db.Close()
```

## Link code&#x20;

Berikut link code lengkap contoh koneksi database MySQL dan PostgreSQL di Golang.

{% embed url="https://github.com/rafli-ramadhan/contact-go/blob/master/db/client.go" %}

{% embed url="https://github.com/rafli-ramadhan/sales-go/blob/master/db/client.go" %}

Reference:

{% embed url="https://stackoverflow.com/questions/4111594/why-always-close-database-connection" %}
