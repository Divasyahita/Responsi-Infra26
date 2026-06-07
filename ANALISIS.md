# ANALISIS RESPONSI INFRASTRUKTUR TEKNOLOGI INFORMASI

## Identitas

Nama: Diva Syahita Mawarni
NIM: H1H024015

## Analisis Permasalahan dan Perbaikan

### 1. Kesalahan Sintaks Docker Compose

**Masalah:** Pada file `docker-compose.yml`, bagian `services` tidak menggunakan tanda titik dua (`:`).

**Penyebab:** YAML membutuhkan format key-value yang valid.

**Perbaikan:** Mengubah:

`services`

menjadi:

`services:`

---

### 2. Konfigurasi Database Host Web1 Salah

**Masalah:** Service `web1` menggunakan `DB_HOST=mysql`.

**Penyebab:** Nama service database yang digunakan adalah `db`, bukan `mysql`.

**Perbaikan:** Mengubah `DB_HOST: mysql` menjadi `DB_HOST: db`.

---

### 3. Path Build Web3 Tidak Sesuai

**Masalah:** Service `web3` menggunakan context `./web33`.

**Penyebab:** Folder `web33` tidak tersedia.

**Perbaikan:** Mengubah menjadi `./web3`.

---

### 4. Kesalahan Indentasi YAML

**Masalah:** Bagian environment pada service database memiliki indentasi yang tidak konsisten.

**Penyebab:** YAML sangat sensitif terhadap spasi.

**Perbaikan:** Menyesuaikan seluruh indentasi agar sejajar.

---

### 5. Kesalahan Konfigurasi Nginx

**Masalah:** Konfigurasi upstream mengarah ke backend yang tidak sesuai.

**Penyebab:** Nama host service tidak cocok dengan nama container pada Docker Compose.

**Perbaikan:** Menyesuaikan nama backend menjadi `web1`, `web2`, dan `web3`.

---

### 6. Kesalahan Port Backend Nginx

**Masalah:** Salah satu backend menggunakan port yang tidak sesuai.

**Penyebab:** Apache pada container berjalan pada port 80.

**Perbaikan:** Mengubah konfigurasi upstream menjadi menggunakan port 80.

---

### 7. Kesalahan Dockerfile Web1

**Masalah:** Image PHP Apache ditulis tidak sesuai.

**Penyebab:** Typo pada nama image.

**Perbaikan:** Mengubah menjadi `php:8.2-apache`.

---

### 8. Kesalahan Dockerfile Web3

**Masalah:** Nama image Docker tidak valid.

**Penyebab:** Typo pada Dockerfile.

**Perbaikan:** Mengubah menjadi `php:8.2-apache`.

---

### 9. Kesalahan File SQL

**Masalah:** Terdapat karakter yang tidak diperlukan pada file inisialisasi database.

**Penyebab:** Format file tidak sesuai SQL.

**Perbaikan:** Membersihkan file SQL agar dapat dieksekusi oleh MySQL.

---

### 10. Identitas Web2 Tidak Sesuai

**Masalah:** Tampilan backend kedua tidak menunjukkan identitas yang benar.

**Perbaikan:** Mengubah label menjadi WEB-2.

---

### 11. Identitas Web3 Tidak Sesuai

**Masalah:** Tampilan backend ketiga tidak menunjukkan identitas yang benar.

**Perbaikan:** Mengubah label menjadi WEB-3.

---

### 12. Pengisian Identitas Praktikan

**Masalah:** Placeholder nama dan NIM belum diisi.

**Perbaikan:** Mengganti dengan identitas praktikan yang sebenarnya.

## Hasil Pengujian

Aplikasi berhasil dijalankan menggunakan Docker Compose.

Perintah pengujian:

`docker compose up -d --build`

`curl localhost:8080`

Hasil menunjukkan load balancer Nginx berhasil meneruskan request ke backend web1, web2, dan web3.

## Kesimpulan

Seluruh permasalahan konfigurasi berhasil dianalisis dan diperbaiki. Sistem dapat dijalankan menggunakan Docker Compose, database dapat diakses oleh seluruh backend, serta Nginx berhasil melakukan load balancing ke tiga web server sesuai spesifikasi yang diberikan.
