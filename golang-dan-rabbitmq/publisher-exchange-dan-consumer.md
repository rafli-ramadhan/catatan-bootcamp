---
description: https://www.rabbitmq.com/tutorials/tutorial-three-go.html
---

# Publisher, Exchange dan Consumer

## Konsep

<figure><img src="../.gitbook/assets/1.png" alt=""><figcaption><p><a href="https://www.rabbitmq.com/tutorials/tutorial-three-python.html">https://www.rabbitmq.com/tutorials/tutorial-three-python.html</a></p></figcaption></figure>

* Work Queues atau Task Queues pada RabbitMQ berguna untuk menghindari resource-intensive task (over-process) yang menyebabkan queue harus menunggu pesan diterima oleh consumer.
* Untuk memahami prinsip queue pada RabbitMQ, kita akan menyimulasikan kompleksitas suatu code dengan jumlah dot yang dikirimkan oleh RabbitMQ, setiap dot-nya akan dihitung 1 detik.
* Pada _code_ di consumer terdapat prefetch yang ada pada bagian QoS. Prefetch adalah sebuah aturan RabbitMQ untuk memastkan bahwa setiap pesan dikirimkan pada service yang sudah menyelesaikan tasknya
* Binding -> relasi antara queue dan exchange

<figure><img src="../.gitbook/assets/1 (2).png" alt=""><figcaption><p><a href="https://www.rabbitmq.com/img/tutorials/bindings.png">https://www.rabbitmq.com/img/tutorials/bindings.png</a></p></figcaption></figure>

## Tipe-tipe exchange

* Fanout -> pesan yang sama dikirim ke beberapa queue yang berbeda. Jadi setiap exhange akan menerima data yang sama banyak dan sama value-nya.
* Direct -> pesan hanya dikirim ke queue tertentu
* Exclusive ->&#x20;
* Exchange auto delete kalau tidak ada queue yang melakukan bind

Queue auto delete kalua tidak ada consumer yang terhubung





{% embed url="https://drive.google.com/file/d/1UTj430qdvUE3vTKijnbCCjhhUaqAZ58V/view?usp=sharing" %}

