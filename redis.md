---
description: https://redis.io/
---

# Golang dan Redis

Redis bisa digunakan untuk caching dan message broker. Cache digunakan untuk menyimpan informasi yang sifatnya sementara.

## Install Redis melalui Docker

[https://hub.docker.com/\_/redis](https://hub.docker.com/\_/redis)

Perlu memiliki docker terlebih dahulu, jalankan docker. Lalu install redis melalui CMD dengan command berikut.

```bash
docker pull redis
```

## Go Redis

[https://github.com/redis/go-redis](https://github.com/redis/go-redis)

## Contoh penggunaan redis pada CMD

![](<.gitbook/assets/image (4) (1).png>)

## Contoh _code_ golang dengan Redis

```go
package main

import (
	"context"
	"encoding/json"
	"log"
	"time"

	"github.com/redis/go-redis/v9"
)

type user struct {
	name string `json:"name"`
	age  int    `json:"age"`
}

var ctx = context.Background()

func main() {
	Client := redis.NewClient(&redis.Options{
		Addr: 		  "localhost:6379",
		Password: 	  "",
		DB:		  	  0,
		DialTimeout:  time.Second*2,
		ReadTimeout:  time.Millisecond*5,
		WriteTimeout: time.Millisecond*10,
	})
	if Client != nil {
		log.Println("Redis Initialized")
	}

	key1 := "datasatu"
	key2 := "datasatu"

	command1 := Client.Set(ctx, key1, 23, time.Second*20)
	if err := command1.Err(); err != nil {
		panic(err)
	}

	res1 := Client.Get(ctx, key1)
	if err :=res1.Err(); err != nil {
		panic(err)
	}

	stringRes, err := res1.Bytes()
	if err != nil {
		panic(err)
	}

	log.Println(string(stringRes))

	newUser := user{
		name: "Umar",
		age:  23,
	}

	marshalStruct, err := json.Marshal(newUser)
	if err != nil {
		panic(err)
	}

	command2 := Client.Set(ctx, key2, marshalStruct, time.Second*20)
	if err := command2.Err(); err != nil {
		panic(err)
	}

	res2 := Client.Get(ctx, key2)
	if err :=res2.Err(); err != nil {
		panic(err)
	}

	bytesRes, err := res2.Bytes()
	if err != nil {
		panic(err)
	}

	var temp user

	err = json.Unmarshal(bytesRes, &temp)
	if err != nil {
		panic(err)
	}

	log.Println(temp)
}
```
