# Buffered Channel

Default channel itu hanya bisa menerima 1 data -> jika ditambah data ke-2, maka kita akan diminta menunggu sampai data ke-1 ada yang mengambil.

Kadang-kadang ada kasus dimana pengirim lebih cepat dibanding penerima, dalam hal ini jika kita menggunakan channel, maka otomatis pengirim akan ikut lambat juga.

Buffered Channel -> buffer yang bisa digunakan untuk menampung data antrian di Channel

## Buffer Capacity

Kita bebas memasukkan berapa jumlah kapasitas antrian di dalam buffer.

Jika kita set misal 5, artinya kita bisa menerima 5 data di buffer.&#x20;

Jika kita mengirim data ke 6, maka kita diminta untuk menunggu sampai buffer ada yang kosong Ini cocok sekali ketika memang goroutine yang menerima data lebih lambat dari yang mengirim data
