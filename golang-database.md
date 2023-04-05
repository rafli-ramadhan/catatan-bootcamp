# Golang Database



Install Go MySQL Driver

```
 go get -u github.com/go-sql-driver/mysql
```

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

Pool -> management access
