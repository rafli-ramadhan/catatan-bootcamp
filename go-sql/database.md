# Golang Native SQL

## SQL Query di Golang dan Query Parameter

Berikut adalah contoh query di Golang Native SQL.

```go
 queryInsert := `insert into pelanggan (name, no_telp) values (?, ?)`
 for i, v := range listContent {
	 _, err := db.ExecContext(ctx, queryInsert, i, v)
	 if err != nil {
		 panic(err)
	 }
 }
```

Pada query di atas terdapat query parameter yang dapat diganti dengan value tertentu. Tujuan adanya query parameter adalah untuk menghindari SQL injection. Jika menggunakan MySQL, query parameter dapat disisipkan di query dengan tanda ?. Lalu value di query dapat di input melalui fungsi ExecContext() untuk query Insert, Update dan Delete atau fungsi QueryContext() untuk query Get seperti code di bawah ini.

Variabel queryInsert di atas dapat diganti dengan query di bawah ini.

```sql
insert into comments (email, comment) value (?,?)
```

```sql
update contact SET name = ?, no_telp = ? where id = ?
```

```sql
delete FROM contact where id = ?
```

Jika menggunakan pgx atau driver Golang untuk database PostgreSQL, query parameter disisipkan di query dengan tanda $1, $2 dan seterusnya sesuai urutan  parameter.

```sql
insert into comments (email, comment) value ($1,$2)
```

```sql
update contact SET name = $1, no_telp = $2 where id = $3
```

```sql
delete FROM contact where id = $1
```

## Prepare Statement

Prepare statment digunakan untuk memastikan query yang di eksekusi berada dalam 1 koneksi database yang sama.

## Database Transaction

Database transaction digunakan supaya SQL yang dikirim tidak langsung di commit ke database. Implementasi database transaction semisal jika kita ingin melakukan insert beberapa database, lalu ada 1 data yang gagal di create. Maka kita bisa menggunakan database transaction untuk me-rollback atau membatalkan create seluruh data yang telah di insert ke database. Database transaction di awali dengan inisiasi berikut.

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

## Link Code

Berikut contoh code penerapan query parameter, prepare statement dan database transaction di Golang.

{% embed url="https://github.com/rafli-ramadhan/contact-go/blob/master/repository/contact_http_db_impl.go" %}

{% embed url="https://github.com/rafli-ramadhan/sales-go/tree/master/repository" %}
