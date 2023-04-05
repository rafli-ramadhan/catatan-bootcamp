# Database

## Query Parameter

Untuk mencegah SQL Injection

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

Supaya SQL yang dikirim tidak langsung di commit ke database
