# Mocking

* Mock -> object yang sudah kita program dengan ekspektasi tertentu sehingga ketika dipanggil, dia akan menghasilkan data yang sudah kita program diawal.
* Mock -> teknik dalam unit testing -> bisa membuat mock object dari suatu object yang memang sulit untuk di testing
* Misal kita ingin membuat unit test, namun ternyata ada kode program kita yang harus memanggil API Call ke third party service. Hal ini sangat sulit untuk di test, karena unit testing kita harus selalu memanggil third party service, dan belum tentu response nya sesuai dengan apa yang kita mau
* Pada kasus seperti ini, cocok sekali untuk menggunakan mock object
