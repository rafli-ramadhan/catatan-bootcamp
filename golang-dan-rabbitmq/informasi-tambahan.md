# Informasi Tambahan

* RabbitMQ akan menghapus queue dan pesan saat berhenti atau crash. Hal tersebut dapat dihindari dengan mengaktifkan message durability pada bagian QueueDeclare di sender.go atau publisher.go menjadi `true`. Dengan begitu pesan dan queue pada RabbitMQ akan dapat bertahan saat RabbitMQ di restart.

```go
        q, err := ch.QueueDeclare(
		"hello", // name
		false,   // durable
		false,   // delete when unused
		false,   // exclusive
		false,   // no-wait
		nil,     // arguments
	)
```
