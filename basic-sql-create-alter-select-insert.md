# Basic SQL (Create, Alter, Select, Insert)

## Create Table

Don't forget -> `auto_increment` not `auto increment`

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

```sql
alter table pelanggan add no_telp varchar(100) not null
```

```sql
alter table pelanggan modify column id int not null auto_increment;l
```

## Select

```sql
select id, name, no_telp from pelanggan
```

## Insert

```sql
insert into pelanggan (name, no_telp) values ("andi", "088227867533")
```

Ada kalanya suatu client dapat melakukan sql _injection_, yaitu dengan mengeksekusi query SQL yang tidak sesuai. Untuk menghindari SQL injection gunakan tanda ?

```sql
insert into comments (email, comment) value (?,?)
```

Pada pgx (PostgreSQL Database Driver) dapat juga menggukan operator $1, $2, dst.

```sql
insert into comments (email, comment) value ($1,$2)
```

Reference :

[https://www.w3schools.com/SQL](https://www.w3schools.com/SQL)
