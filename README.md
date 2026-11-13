# Ayam Geprek Romeesa

Aplikasi web pemesanan dan manajemen operasional restoran berbasis CodeIgniter 3.

## Struktur proyek

```text
application/
  config/        Konfigurasi aplikasi, URL, database, dan routing
  controllers/   Alur fitur: autentikasi, kasir, dapur, pemilik, pelanggan
  models/        Akses data dan logika model
  views/         Halaman aplikasi
    templates/   Kerangka/layout halaman staf
assets/
  css/           Gaya antarmuka
  js/            Interaksi antarmuka
uploads/         Foto menu yang digunakan aplikasi
system/          Framework CodeIgniter 3; jangan ubah untuk perbaikan fitur
db_ayam_geprek.sql
                Skema dan data awal database
index.php        Front controller dan pemilih environment
```

Folder `application/cache/` dan `application/logs/` adalah folder runtime. Jangan
menaruh kode fitur di dalamnya. `readme.rst` dan `composer.json` berasal dari
distribusi CodeIgniter; untuk petunjuk aplikasi, gunakan README ini.

## Mencari sumber masalah

Telusuri dari halaman atau alur yang bermasalah, lalu ikuti urutannya:

1. `application/views/` — tampilan, form, dan tautan halaman.
2. `application/controllers/` — validasi input, hak akses, alur proses, dan respons.
3. `application/models/` — operasi data bila fitur menggunakan model.
4. `application/config/routes.php` — pemetaan URL ke controller.
5. `application/config/database.php` dan `db_ayam_geprek.sql` — koneksi serta
   struktur/data database.
6. `application/logs/` — log aplikasi saat terjadi error.

| Area fitur | Controller | View utama |
| --- | --- | --- |
| Login dan sesi | `Auth.php` | `v_login.php` |
| POS, antrean bayar, struk, laporan kasir | `Cashier.php` | `v_cashier*.php`, `v_laporan.php`, `v_struk.php` |
| Pesanan pelanggan dan status pesanan | `Pelanggan.php` | `v_pelanggan*.php` |
| Antrean dan penyelesaian pesanan dapur | `Kitchen.php` | `v_kitchen.php` |
| Laporan, menu, pengguna, meja | `Owner.php` | `v_owner*.php` |

Nama file controller dan view yang dirujuk aplikasi harus tetap sesuai dengan
konvensi CodeIgniter dan pemanggilan yang ada. Sebelum memindahkan atau mengganti
nama file, cari semua referensinya dan perbarui routing/pemanggilnya bersama-sama.

## Menjalankan secara lokal dengan XAMPP

1. Nyalakan Apache dan MySQL melalui XAMPP.
2. Buat atau impor database menggunakan `db_ayam_geprek.sql` melalui phpMyAdmin.
3. Sesuaikan host, nama database, username, dan password di
   `application/config/database.php`.
4. Sesuaikan `$config['base_url']` di `application/config/config.php` dengan URL
   folder proyek di mesin lokal.
5. Buka URL proyek melalui browser.

Untuk memakai PHP CLI dari instalasi XAMPP:

```powershell
C:\xampp\php\php.exe -l application\controllers\Cashier.php
```

Ganti nama file pada perintah tersebut sesuai file PHP yang diubah. Pemeriksaan
sintaks tidak menggantikan pengujian alur fitur melalui browser.

## Checklist saat memperbaiki defect

- Catat peran pengguna, URL, langkah untuk mengulang masalah, hasil yang
  diharapkan, dan hasil yang benar-benar terjadi.
- Periksa log terbaru di `application/logs/` dan pesan error di browser.
- Ikuti alur tampilan → controller → model/database; periksa routing bila URL
  tidak menuju halaman yang benar.
- Periksa perubahan skema database bersama query yang memakai tabel/kolomnya.
- Uji alur yang diperbaiki dan alur terkait untuk memastikan tidak ada regresi.
- Jangan mengubah `system/` untuk memperbaiki perilaku aplikasi kecuali perubahan
  framework memang disengaja dan dampaknya sudah ditinjau.
- Sebelum mengubah database, buat cadangan data yang diperlukan. Jangan
  mengimpor ulang dump pada database berisi data penting tanpa memahami dampaknya.

## Antarmuka

Catatan bahasa visual dan komponen antarmuka berada di [DESIGN.md](DESIGN.md).
