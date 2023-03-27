# Buffered Channel

Default channel itu hanya bisa menerima 1 data -> jika ditambah data ke-2, maka kita akan diminta menunggu sampai data ke-1 ada yang mengambil.

Kadang-kadang ada kasus dimana pengirim lebih cepat dibanding penerima, dalam hal ini jika kita menggunakan channel, maka otomatis pengirim akan ikut lambat juga&#x20;

Buffered Channel -> buffer yang bisa digunakan untuk menampung data antrian di Channel
