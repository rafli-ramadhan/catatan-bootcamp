# Create & Alter Table

```sql
create table pelanggan (
	id varchar(100) not null,
	name varchar(100) not null,
	primary key (id)
)
```

```sql
alter table pelanggan add no_telp varchar(100) not null
```

```sql
alter table pelanggan modify column id int not null auto_increment;l
```
