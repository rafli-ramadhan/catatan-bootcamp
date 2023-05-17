# Golang Native SQL

## Query Parameter

Untuk mencegah SQL Injection -> SQL injection adalah teknik untuk mencari celah keamanan melalui SQL query.

```go
 queryInsert := `insert into pelanggan (name, no_telp) values (?, ?)`
 for i, v := range listContent {
	 _, err := db.ExecContext(ctx, queryInsert, i, v)
	 if err != nil {
		 panic(err)
	 }
 }
```

## Prepare Statement

Untuk memastikan query yang di eksekusi berada dalam 1 koneksi yang sama

```go
 db := client.GetDB("mysql").GetMysqlConnection()

 queryInsert := `insert into pelanggan (name, no_telp) values (?, ?)`
 prepareMysql, err := db.PrepareContext(ctx, queryInsert)
 for i, v := range listContent {
 _, err := prepareMysql.ExecContext(ctx, i, v)
 if err != nil {
 	 panic(err)
 	 }
 }
```

## Database Transaction

Database transaction Supaya SQL yang dikirim tidak langsung di commit ke database. Database transaction di awali dengan inisiasi berikut.

```go
trx, err := db.BeginTx(ctx, nil)
if err != nil {
	panic(err) // bisa diganti dengan fmt atau log
}
```

Query dapat di commit dengan _code_ berikut.

```go
trx.Commit()
```

Namun, ada kalanya ingin dilakukan pengecekan untuk menghindari error. Jika error terjadi dapat di atasi dengan _code_ berikut.

```go
if err != nil {
    trx.Rollbacck()
}
```

## Contoh _code_ lengkap implementasi query, prepare statement dan database transaction

[https://github.com/rafli-ramadhan/sales-go/tree/master/repository](https://github.com/rafli-ramadhan/sales-go/tree/master/repository)
