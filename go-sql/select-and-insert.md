# Select & Insert

## Select

```sql
select id, name, no_telp from pelanggan
```

## Insert

```sql
insert into pelanggan (name, no_telp) values ("andi", "088227867533")
```

Untuk menghindari SQL injection gunakan ?

```sql
insert into comments (email, comment) value (?,?)
```



