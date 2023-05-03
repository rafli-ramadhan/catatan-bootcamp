# Golang Database Driver

## Golang Database Package

Golang memiliki beberapa driver untuk koneksi database, diantarnya :

1. MySQL

Untuk instalasi dan set up bisa klik link berikut.

[https://github.com/go-sql-driver/mysql](https://github.com/go-sql-driver/mysql)

2. PostgreSQL

Untuk instalasi dan set up bisa klik link berikut.

[https://github.com/jackc/pgx](https://github.com/jackc/pgx)

## Golang Database Pool

Database pool digunakan untuk management access

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

```go
// to prevent connection leak
defer db.Close()
```

## Link _code_&#x20;

Berikut link _code_ lengkap koneksi database MySQL dan PostgreSQL dan contoh env-nya.

[https://github.com/rafli-ramadhan/sales-go/blob/master/db/client.go](https://github.com/rafli-ramadhan/sales-go/blob/master/db/client.go)
