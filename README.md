# Web Absensi Peserta Magang — BPS Kota Padang Panjang

Sistem absensi peserta magang berbasis web (PHP native + MySQL) dengan kunci lokasi GPS, pengajuan izin/sakit/absen manual dengan persetujuan admin, catatan kegiatan harian, dan rekap/ekspor Excel berformat surat resmi.

---

## Hak Cipta (Copyright)

**Copyright © 2026 pu4s0. All Rights Reserved.**

Seluruh kode sumber, struktur database, desain antarmuka, dan dokumentasi dalam proyek ini adalah karya **pu4s0** dan dilindungi hak cipta.

Tanpa izin tertulis dari pemilik hak cipta, dilarang:
- menyalin, memperbanyak, atau mendistribusikan proyek ini, seluruhnya maupun sebagian;
- memodifikasi atau membuat karya turunan dari proyek ini;
- menjual, menyewakan, atau mengklaim proyek ini sebagai karya sendiri;
- menghapus atau mengubah pernyataan hak cipta ini, termasuk teks hak cipta pada footer aplikasi.

Penggunaan oleh BPS Kota Padang Panjang sebagai sarana absensi peserta magang diizinkan sebatas penggunaan internal di lingkungan instansi tersebut.

**Pengecualian (bukan bagian dari hak cipta di atas):**
- **Logo dan nama Badan Pusat Statistik** adalah milik BPS dan tidak termasuk dalam klaim hak cipta proyek ini.
- **Pustaka pihak ketiga** (jQuery, DataTables, MapLibre GL JS, OpenStreetMap, dan lainnya) tetap tunduk pada lisensinya masing-masing.

Untuk izin penggunaan di luar ketentuan ini, hubungi pemilik hak cipta (pu4s0).

---

## Fitur

### Peserta
- Login dan signup (foto profil, NIM, jurusan, asal universitas, pilihan mentor dari data pegawai)
- Absen masuk/pulang dengan **kunci lokasi GPS** (radius diatur di `includes/config.php`) dan peta interaktif (MapLibre GL)
- Absen pulang dapat diklik ulang; jam pulang selalu diperbarui ke klik terakhir
- Notifikasi popup setelah absen berhasil
- Pengajuan **absen manual**, **izin**, dan **sakit** (maksimal 7 hari ke belakang) dengan persetujuan admin
- **Catatan kegiatan harian** (tambah, edit, hapus untuk kegiatan hari ini)
- Status "Tidak Hadir" otomatis untuk hari kerja tanpa absensi
- Riwayat absensi (DataTables, filter tanggal) dan unduh Excel pribadi
- Kelola profil dan ganti password
- Tampilan responsif untuk HP

### Admin
- Dashboard rekap peserta, rekap absen harian, dan rekap absen bulanan
- Notifikasi dan persetujuan pengajuan
- Tambah, ubah, hapus (termasuk hapus massal), dan reset password peserta
- Unduh Excel harian dan bulanan dengan kop surat dan tanda tangan Mentor serta Kasubag Umum
- Tabel catatan kegiatan pada semua file Excel
- Ganti password admin

---

## Teknologi
PHP native (mysqli, prepared statements), MySQL/MariaDB, DataTables, MapLibre GL JS, OpenStreetMap.

## Instalasi Singkat (Laragon)
1. Letakkan folder proyek di `C:\laragon\www\`.
2. Jalankan Apache dan MySQL, lalu impor `database.sql` (HeidiSQL atau phpMyAdmin).
3. Sesuaikan `includes/db.php` (host, user, password, nama database).
4. Atur `KANTOR_LAT`, `KANTOR_LNG`, dan `RADIUS_METER` di `includes/config.php`.
5. Buka `http://localhost/web-absensi-magang/`.
6. Login admin awal: `admin` / `password`, **segera ganti** lewat menu Ganti Password.

GPS di HP membutuhkan **HTTPS** (misalnya ngrok atau hosting dengan SSL).

## Struktur Singkat
```
├── index.php, login.php, signup.php, admin_login.php
├── dashboard_peserta.php, absen.php, kelola_profil.php, ...
├── admin_dashboard.php, peserta_admin.php, rekap_bulanan.php, ...
├── export_peserta.php, export_harian.php, export_bulanan.php
├── includes/   (db, auth, config, helper, footer)
├── assets/     (css, img, uploads)
└── database.sql
```

---

© 2026 pu4s0. All Rights Reserved.
