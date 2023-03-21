# HTTP Stateless

HTTP merupakan stateless antara client dan server -> artinya server tidak akan menyimpan data apapun untuk mengingat setiap request dari client

Tujuannya -> agar mudah melakukan scalability di sisi server.

Lantas bagaimana caranya agar server bisa mengingat sebuah client? Misal ketika kita sudah login di website, server otomatis harus tahu jika client tersebut sudah login, sehingga request selanjutnya, tidak perlu diminta untuk login lagi.

Solusinya -> bisa memanfaatkan Cookie
