# Create Table and Alter Table

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
