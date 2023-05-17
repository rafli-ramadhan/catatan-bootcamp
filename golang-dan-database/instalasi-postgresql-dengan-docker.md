---
description: https://hub.docker.com/_/postgres/
---

# Instalasi PostgreSQL dengan Docker

Jalankan docker terlebih dahulu. Untuk pengguna docker dekstop bisa langsung membuka aplikasi, maka docker akan running dengan sendirinya. Lalu buka CMD, bash atau powershell dan eksekusi _code_ berikut.

```
docker pull postgres
```

Setelah itu buat volume untuk menyimpan data. Untuk pengguna docker dekstop dapat meng-klik tab volume. Lalu buat volume baru, misal dengan nama postgres-volume.

<figure><img src="../.gitbook/assets/postgres volume.png" alt=""><figcaption></figcaption></figure>

Setelah itu set konfigurasi database dengan format di bawah ini di CMD, bash atau _powershell_. Untuk bagian some-postgres dan your\_password dapat di ubah sesuai keinginan.

```
docker run --name some-postgres -e POSTGRES_PASSWORD=your_password -p 5432:5432 -v postgres-volume:/var/lib/postgresql/data -d postgres
```
