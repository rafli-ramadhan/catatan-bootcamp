---
description: Create Table, Alter Table, Select, Insert, Update, Delete dan SQL Injection
---

# Basic SQL

## Create Table

Contoh SQL untuk membuat tabel baru bernama pelanggan dan comments :

```sql
create table pelanggan (
	id varchar(100) not null,
	name varchar(100) not null,
	primary key (id)
)
```

```sql
create table comments (
	idcomment int not null auto_increment,
	email varchar(100) not null,
	comment varchar(100) not null,
	primary key (idcomment)
)
```

## Alter

Contoh alter untuk menambah kolom :

```sql
alter table pelanggan 
add no_telp varchar(100) not null
```

Contoh alter untuk modifikasi kolom :

```sql
alter table pelanggan 
modify column id int not null auto_increment;
```

Contoh alter untuk menambahkan kolom foreign key bernama id\_2 di tabel\_A yang nilainya dari kolom id di tabel\_B :

```sql
alter table table_A
add constaint table_B
foregn key id_2 references table_B(id)
```

## Select

Contoh mendapatkan data dari tabel pelanggan yang memiliki kolom id, name dan no\_telp :

```sql
select id, name, no_telp from pelanggan
```

## Insert

Contoh insert data baru ke tabel pelanggan yang memiliki kolom id, name dan no\_telp :

```sql
insert into pelanggan (name, no_telp) values ("andi", "088227867533")
```

## Update

Contoh untuk update data dari tabel contact kolom name dan no\_telp dengan id tertentu :

```sql
update contact SET name = "umar" , no_telp = "089932943287" where id = 1
```

## Delete

Contoh untuk menghapus data semua kolom dari tabel contact dengan id = 1

```sql
delete FROM contact where id = 1
```

## Insert Query di Golang

Ada kalanya suatu client dapat melakukan sql _injection_, yaitu dengan mengeksekusi query SQL yang tidak sesuai. Untuk menghindari SQL injection gunakan tanda "?" seperti berikut.

```sql
insert into comments (email, comment) value (?,?)
```

```sql
update contact SET name = ?, no_telp = ? where id = ?
```

```sql
delete FROM contact where id = ?
```

Pada pgx (PostgreSQL Database Driver) dapat juga menggukan operator $1, $2, dst.

```sql
insert into comments (email, comment) value ($1,$2)
```

```sql
update contact SET name = $1, no_telp = $2 where id = $3
```

```sql
delete FROM contact where id = $1
```

Reference :

[https://www.w3schools.com/SQL](https://www.w3schools.com/SQL)
