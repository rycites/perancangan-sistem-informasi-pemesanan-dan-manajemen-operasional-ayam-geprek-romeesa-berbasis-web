# Arah Desain Antarmuka

Catatan ini menjelaskan bahasa visual yang dipakai di seluruh halaman, supaya
halaman baru tetap konsisten dengan yang sudah ada.

## Acuan

Acuan tampilan adalah dasbor pemesanan makanan: sidebar indigo gelap, pil menu
aktif berwarna kuning, latar lavender muda, kartu putih bersudut lembut, dan
tombol utama indigo. Yang diambil adalah bahasa visualnya. Isi, merek, dan
tata letak spesifik acuan tidak ditiru; strukturnya dipetakan ke halaman yang
memang sudah ada di aplikasi ini.

## Palet

| Token | Nilai | Dipakai untuk |
| --- | --- | --- |
| `--bg` | `#eff0fb` | latar halaman |
| `--surface` | `#ffffff` | kartu dan panel |
| `--surface-2` | `#f7f8fd` | baris tabel, isian dalam kartu |
| `--border` | `#e3e5f4` | garis tepi kartu dan kolom |
| `--ink` | `#16123a` | teks utama |
| `--ink-2` | `#5c5a7d` | teks pendamping |
| `--ink-3` | `#6f6d8c` | teks kecil, label kolom |
| `--brand` | `#4f46e5` | aksi utama, tautan, menu aktif |
| `--brand-strong` | `#4338ca` | keadaan hover/tekan |
| `--brand-soft` | `#eceafd` | latar lembut bernuansa utama |
| `--accent` | `#f5d949` | pil menu aktif, penanda meja, sorotan |
| `--sidebar` | `#1c1240` | sidebar dan bilah atas pelanggan |
| `--sidebar-raise` | `#271a55` | kartu di dalam sidebar |

Warna inti hanya dua, indigo dan kuning, sisanya netral. Hijau, kuning tua, dan
merah hanya dipakai untuk status (lunas, menunggu, gagal), bukan hiasan.

## Tipografi

Satu keluarga huruf: Plus Jakarta Sans (400 sampai 800), dengan cadangan
Segoe UI dan font sistem. Nama restoran ditulis miring tebal sebagai penanda
merek, tanpa gambar logo.

Ukuran: 13px untuk meta, 14-15px untuk teks, 16px judul kartu, 20px judul
seksi, 24-28px judul halaman, 32px angka ringkasan. Angka uang memakai
`font-variant-numeric: tabular-nums` supaya kolom nominal rata.

## Bentuk dan Jarak

Sudut membulat 10px (kontrol), 14px (kartu kecil), 18-20px (kartu dan panel).
Bayangan lembut dan tipis, bukan efek menyala. Jarak mengikuti kelipatan 4px.

## Tata Letak

Panel staf: sidebar 264px yang tetap di tempat, bilah atas memuat judul
halaman dan menu pengguna, lalu isi halaman. Di bawah 992px sidebar berubah
menjadi panel geser dengan tombol pembuka, latar gelap, dan tombol tutup.

Halaman pelanggan: bilah atas gelap yang menempel, kolom pencarian dan chip
kategori, grid menu, bilah keranjang melayang di bawah untuk layar kecil, dan
keranjang berbentuk panel geser dari kanan di semua ukuran layar.

## Aturan Komponen

- Tidak ada kontrol tanpa fungsi. Kolom pencarian, chip kategori, dan pemilih
  pembayaran benar-benar bekerja.
- Setiap daftar punya keadaan kosong dengan penjelasan dan satu langkah
  lanjutan.
- Badge status selalu memuat titik warna dan teks, tidak hanya warna.
- Setiap isian punya label, dan fokus keyboard terlihat jelas.
- Nomor faktur, nominal, dan jumlah memakai angka rata kolom.

## Catatan Kontras

Diukur dengan pemeriksa kontras: teks utama di latar halaman 15.68:1, di kartu
17.77:1, teks pendamping 6.53:1, teks kecil 4.95:1, putih di atas indigo
6.29:1, teks gelap di atas kuning 12.61:1, teks sidebar 10.50:1. Status hijau
5.28:1, kuning tua 5.02:1, merah 4.83:1. Semua memenuhi ambang 4.5:1 untuk
teks normal.

## Berkas

- `assets/css/theme.css` : token, kerangka, dan seluruh komponen
- `assets/js/theme.js` : panel geser dan penyaring daftar menu
- `application/views/templates/v_sidebar*.php` : kerangka panel staf
