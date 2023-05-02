# Logging

Logging digunakan untuk mencatat aktivitas yang terjadi di server. Contohnya saat suatu endpoint di hit, dapat ditampilkan logging request dari client.

Logging diterapkan di middleware, karena semua proses yang terjadi di server akan melewati middleware terlebih dahulu.

Jenis-jenis logging di Golang berdasarkan kepopulerannya di Github:

1. [https://github.com/sirupsen/logrus](https://github.com/sirupsen/logrus)
2. [https://github.com/uber-go/zap](https://github.com/uber-go/zap)
3. [https://github.com/rs/zerolog](https://github.com/rs/zerolog)

Golang juga memiliki bawaan package log sendiri bernama "log". Perbedaan log dan fmt yaitu log dapat menampilkan waktu suatu kode dieksekusi. Perlu diperhatikan juga bahwa log digunakan untuk logging sementara fmt untuk formatting. Selain itu, jika dilihat dari code log(...),&#x20;

Reference :

[https://stackoverflow.com/questions/19646889/why-should-i-use-log-println-instead-of-fmt-println#:\~:text=Two%20things%20are%20different%3A%20Printing%20via%20package%20log,log%20is%20for%20logging%20and%20fmt%20for%20formatting.](https://stackoverflow.com/questions/19646889/why-should-i-use-log-println-instead-of-fmt-println)
