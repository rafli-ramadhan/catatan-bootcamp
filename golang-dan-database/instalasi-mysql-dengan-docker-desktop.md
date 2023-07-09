# Instalasi MySQL dengan Docker Desktop

Jalankan docker desktop, lalu buka tab search dan cari image MySQL.

<figure><img src="../.gitbook/assets/docker mysql.png" alt=""><figcaption></figcaption></figure>

Selanjutnya pull image MySQL dan tunggu sampai proses download selesai. Setelah proses download selesai, image MySQL akan otomatis muncul di tab Images.

<figure><img src="../.gitbook/assets/Docker mysql images.png" alt=""><figcaption></figcaption></figure>

Selanjutnya jalankan Images tersebut dengan setting sebagai berikut.

<figure><img src="../.gitbook/assets/docker mysql run.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/docker mysql env.png" alt=""><figcaption></figcaption></figure>

Lalu klik run dan cek tab container untuk memastikan container MySQL sudah berjalan.

<figure><img src="../.gitbook/assets/docker mysql image.png" alt=""><figcaption></figcaption></figure>

Gunakan GUI seperti DBeaver untuk cek koneksi MySQL. Untuk URL dapat diisi dengan format berikut. Nama database diisi dengan nama database yang sama saat mengisi optional setting env saat ingin running image MySQL.

```
jdbc:mysql://localhost:3306/nama_database?allowPublicKeyRetrieval=true
```

<figure><img src="../.gitbook/assets/Dbeaver.png" alt=""><figcaption></figcaption></figure>
