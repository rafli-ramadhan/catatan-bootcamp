# Setting RabbitMQ

## Auto Delete

Auto delete merupakan setting dari RabbitMQ yang memungkinkan queue yang tidak terpakai akan langsung di delete. Setting auto delete bisa dilakukan dari sisi publisher atau consumer pada code QueueDeclare.

<pre class="language-go"><code class="lang-go"><strong>        q, err := ch.QueueDeclare(
</strong>		"task_queue", // name
		true,         // durable
		false,        // auto delete queue when unused
		false,        // exclusive
		false,        // no-wait
		nil,          // arguments
	)
	failOnError(err, "Failed to declare a queue")
</code></pre>



## Acknowledge

AutoAck bisa di setting di _code_ receiver atau consumer pada bagian Consume.

```go
        msgs, err := ch.Consume(
		q.Name, // queue
		"",     // consumer
		false,  // auto-ack
		false,  // exclusive
		false,  // no-local
		false,  // no-wait
		nil,    // args
	)
	failOnError(err, "Failed to register a consumer")
```



