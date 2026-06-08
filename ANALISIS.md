# Analisis Perbaikan

## Permasalahan 1
### Gejala
docker compose gagal parse, tidak ada container yang berjalan.
### Penyebab
Kata `services` pada docker-compose.yml tidak memiliki tanda titik dua.
### Solusi
Mengubah `services` menjadi `services:`.

---

## Permasalahan 2
### Gejala
web1 gagal terhubung ke database.
### Penyebab
DB_HOST pada web1 diisi `mysql`, padahal nama service database adalah `db`.
### Solusi
Mengubah `DB_HOST: mysql` menjadi `DB_HOST: db`.

---

## Permasalahan 3
### Gejala
web2 gagal terhubung ke database.
### Penyebab
DB_PASS pada web2 diisi `wrongpassword`, bukan password yang benar.
### Solusi
Mengubah `DB_PASS: wrongpassword` menjadi `DB_PASS: student123`.

---

## Permasalahan 4
### Gejala
web3 gagal build image.
### Penyebab
Build context pada web3 mengarah ke folder `./web33` yang tidak ada.
### Solusi
Mengubah `context: ./web33` menjadi `context: ./web3`.

---

## Permasalahan 5
### Gejala
nginx tidak bisa meneruskan request ke web3.
### Penyebab
web3 tidak terdaftar di network `frontend` sehingga nginx tidak bisa menjangkaunya.
### Solusi
Menambahkan network `frontend` pada service web3.

---

## Permasalahan 6
### Gejala
db container gagal start karena volume error.
### Penyebab
Nama volume tidak konsisten, didefinisikan sebagai `database-data` tapi dipakai sebagai `db-data`.
### Solusi
Menyamakan nama volume menjadi `db-data`.

---

## Permasalahan 7
### Gejala
web1 dan web3 gagal build image.
### Penyebab
Typo pada Dockerfile, `php:8.2-apach` (web1) dan `php:8.2-apche` (web3).
### Solusi
Mengubah keduanya menjadi `php:8.2-apache`.

---

## Permasalahan 8
### Gejala
nginx gagal start dengan error "unknown directive ```nginx".
### Penyebab
File nginx.conf mengandung markdown backtick (```nginx) di awal dan (```) di akhir.
### Solusi
Menghapus backtick markdown dari nginx.conf.

---

## Permasalahan 9
### Gejala
nginx tidak bisa meneruskan request ke web1.
### Penyebab
Upstream nginx mengarah ke `web11:80` (typo), seharusnya `web1:80`.
### Solusi
Mengubah `web11:80` menjadi `web1:80`.

---

## Permasalahan 10
### Gejala
nginx tidak bisa meneruskan request ke web3.
### Penyebab
Upstream nginx menggunakan port `8080` untuk web3, seharusnya port internal `80`.
### Solusi
Mengubah `web3:8080` menjadi `web3:80`.

---

## Permasalahan 11
### Gejala
Output web2 menampilkan WEB-WEB, web3 menampilkan WEB-WOB.
### Penyebab
Typo pada file index.php di web2 dan web3.
### Solusi
Mengubah WEB-WEB menjadi WEB-2 dan WEB-WOB menjadi WEB-3.
