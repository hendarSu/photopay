# Photopay

Photopay adalah platform jual-beli foto lokal yang memudahkan seller dan buyer untuk saling berbagi, menjual, dan membeli koleksi foto dengan cepat dan aman.

## Ringkasan

Photopay dirancang untuk: penjual (seller) mengunggah foto dan menetapkan harga; pembeli (buyer) mencari foto, melakukan pembayaran cepat melalui fitur "Jajan Photo", lalu mengunduh hasil pembelian secara langsung. Sistem mendukung pembelian paket multi-angle (select all angle) dalam satu transaksi.

## Fitur Utama

- Marketplace foto lokal: seller dapat meng-upload foto, menambahkan metadata (judul, deskripsi, tag, kategori, angle), dan menetapkan harga per item atau paket.
- Mekanisme "Jajan Photo": metode pembayaran mikro/sekali klik yang memudahkan pembelian foto tunggal atau paket tanpa proses checkout panjang.
- Select all angle: buyer dapat memilih seluruh variasi angle (mis. front, side, detail) dari sebuah sesi foto dan membayar sekaligus.
- Pencarian dan filter cepat: pencarian berdasarkan kata kunci, kategori, tag, lokasi, dan harga.
- Unduhan instan: setelah pembayaran terkonfirmasi, buyer dapat langsung mendownload file foto beresolusi penuh.
- Dashboard untuk seller & buyer: riwayat transaksi, manajemen foto, laporan penjualan, dan pengaturan pembayaran.
- Harga ditetapkan oleh seller: seller bebas menentukan harga per foto atau paket angle.
- Sistem pembayaran mudah: integrasi gateway pembayaran (placeholder) atau saldo internal (wallet) untuk transaksi cepat.

## Kontrak singkat (inputs/outputs)

- Input: data user (seller/buyer), file foto (+ metadata), pengaturan harga, permintaan pencarian, perintah pembelian.
- Output: halaman daftar foto, detail produk, proses pembayaran, status transaksi, link unduhan untuk file yang dibeli.
- Error modes: stok/file tidak ditemukan, pembayaran gagal, limit bandwidth/akses, hak cipta/dispute.

## Kasus Edge (penting)

- Foto duplikat atau konflik metadata.
- Pembayaran gagal atau timeout saat proses "Jajan Photo".
- Buyer mencoba mengunduh tanpa hak akses.
- Seller menarik foto setelah ada pesanan yang belum diproses.
- Batas ukuran file unggahan terlalu besar.

## Instalasi / Setup Project

Asumsi: macOS dengan Zsh (sesuai lingkungan kerja). Proyek ini adalah aplikasi Laravel; langkah berikut menuntun Anda menyiapkan environment dasar.

Prasyarat

- PHP 8.1+ (atau versi yang sesuai dengan composer.json)
- Composer
- Node.js 16+ dan npm / Yarn
- SQLite (default) atau MySQL/Postgres
- Git

Langkah cepat

1. Salin file environment dan atur variabel

```bash
cp .env.example .env
```

2. Install dependensi PHP

```bash
composer install --prefer-dist --no-interaction
```

3. Generate application key

```bash
php artisan key:generate
```

4. Siapkan database (contoh: SQLite cepat untuk development)

```bash
touch database/database.sqlite
# lalu set DB_CONNECTION=sqlite di .env
```

Jika menggunakan MySQL/Postgres, ubah konfigurasi di `.env` sesuai kredensial Anda.

5. Jalankan migrasi dan seeder

```bash
php artisan migrate --seed
```

6. Install dependensi JavaScript dan build aset

```bash
npm install
npm run build    # atau `npm run dev` untuk mode development
```

7. Buat symbolic link ke storage (untuk akses file publik)

```bash
php artisan storage:link
```

8. Jalankan server lokal

```bash
php artisan serve
```

9. Menjalankan test cepat

```bash
php artisan test
```

Catatan: Jika Anda menggunakan gateway pembayaran pihak ketiga, konfigurasikan kredensialnya di `.env` dan ikuti dokumentasi gateway untuk sandbox/live.

## Cara pakai singkat

1. Daftar sebagai user. Pilih peran: buyer atau seller.
2. Seller: unggah foto, tambahkan metadata, tentukan harga atau paket angle.
3. Buyer: cari foto, gunakan filter, pilih foto/angle yang diinginkan.
4. Buyer gunakan fitur "Jajan Photo" untuk checkout cepat (atau gunakan wallet/gateway).
5. Setelah pembayaran berhasil, buyer dapat mengunduh foto dari halaman transaksi.

## Hal lain / Pengembangan lebih lanjut

- Integrasi gateway pembayaran (Stripe, Midtrans, Xendit, dsb.).
- Sistem review & rating untuk seller.
- Proteksi DRM dan watermark opsional untuk preview publik.
- Paket lisensi (komersial, editorial, personal).
- Penjadwalan promosi, diskon, dan bundling otomatis.

## Kontribusi

Silakan buka issue atau pull request. Ikuti standar coding dan jalankan test sebelum mengirim PR.

## Lisensi

Lisensi proyek ini mengikuti file `composer.json` dan/atau LICENSE jika tersedia.

