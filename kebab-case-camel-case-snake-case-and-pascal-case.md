# Kebab Case, Camel Case Snake Case & Pascal Case

* Kebab case biasa digunakan pada penamaan file seperti di bawah ini yang dapat dikenali dengan tanda "-" sebagai pemisah antar kata.

```
file-handler.go
```

```
user-repo.go
```

* Camel case biasa digunakan pada deklarasi variabel yang diawali dengan huruf kecil dan untuk kata berikutnya diawali dengan huruf besar serta antar kata tidak diberi spasi. Contohnya seperti di bawah ini.

```go
var userName string = "member_01"
```

* Snake case biasa digunakan di JSON yang dikenali dengan adanya "\_" sebagai pemisah antar kata. Contohnya seperti di bawahi ini.

```json
{
    "user_name": "member_01",
}
```

* Pascal case biasa digunakan pada parameter struct di Golang. Hampir mirip dengan camel case, bedanya diawali dengan huruf besar. Contohnya di bawah ini.

```go
type User struct {
    FullName string // pascal case
}
```
