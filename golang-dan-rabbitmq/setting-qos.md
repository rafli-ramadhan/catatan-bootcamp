# Setting QoS

Setting QoS dapat dilihat pada link berikut [https://github.com/rabbitmq/rabbitmq-tutorials/blob/main/go/worker.go](https://github.com/rabbitmq/rabbitmq-tutorials/blob/main/go/worker.go). Untuk uji coba diperlukan 1 publisher dan setidaknya 2 consumer.

```go
        err = ch.Qos(
		1,     // prefetch count
		0,     // prefetch size
		false, // global
	)
	failOnError(err, "Failed to set QoS")
```

time millisecond\*20

Setting QoS dan&#x20;

* QOS true ^ auto-act true -> round robin
* QOS true ^ auto-act false -> tidak round robin
* QOS false ^ auto-act true -> round robin
* QOS false ^ auto-act false -> round robin

