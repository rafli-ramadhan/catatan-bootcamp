# Command di Golang

## Inisiasi Go Module

Inisiasi go module :

```
go mod init nama_project
```

Buat file main.go, kemudian lakukan running

## Running Go Module

```
go run main.go
```

atau

```
go run .
```

atau bisa menggunakan go build lalu start main.

```
go build main.go
```

```
start main
```

## Download Module

```
go mod download && go mod tidy
```

Kegunaan `go mod tidy` :

* Untuk memastikan modul yang ada di go.mod sesuai dengan souce code.
* Untuk menambahkan modul yang dibutuhkan tapi belum ada di package.

## Go Get vs Go Mod Download

[https://stackoverflow.com/questions/66356034/what-is-the-difference-between-go-get-command-and-go-mod-download-command](https://stackoverflow.com/questions/66356034/what-is-the-difference-between-go-get-command-and-go-mod-download-command)
