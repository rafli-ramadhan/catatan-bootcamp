# Close Database

## Kenapa koneksi database perlu di close ?

Dalam inisiasi database pastinya ada database management pool yang mengizinkan berapa banyak koneksi yang terhubung ke database. Koneksi perlu segera mungkin di close setelah menggunakan database, agar bisa digunakan untuk koneksi yang lain.

Reference:

{% embed url="https://stackoverflow.com/questions/4111594/why-always-close-database-connection" %}
