E-PRESENSI GTK - PWA PACKAGE
============================

Isi paket:
- index.html: file index_ok.html dengan metadata PWA dan pendaftaran service worker.
- manifest.webmanifest: identitas dan pengaturan instalasi PWA.
- service-worker.js: cache shell aplikasi; tidak menyimpan request POST backend.
- icons/: ikon 192x192 dan 512x512.

FITUR YANG DIPERTAHANKAN
- Aplikasi dan alur yang sudah ada di index_ok.html.
- Backend Google Apps Script yang sudah terkonfigurasi di file sumber.
- Scanner QR, GPS, role akses, pengaturan, rekap, dan ekspor sesuai implementasi sumber.
- Desain/struktur visual sumber dipertahankan.

PENTING: STATUS BACKEND
- File sumber menetapkan IS_PREVIEW = false.
- File sumber memiliki GAS_URL berformat URL Web App Google Apps Script (/exec).
- Pemeriksaan file HTML saja tidak membuktikan bahwa deployment GAS aktif, dapat diakses oleh pengguna yang dituju, memakai Spreadsheet yang benar, atau bahwa semua action API berhasil.
- Sebelum produksi, uji login, pemuatan data, simpan/edit data GTK, pengaturan, scan QR + GPS, pengajuan/persetujuan izin, riwayat, dan ekspor pada akun uji. Pastikan data dari dua perangkat masuk ke Spreadsheet yang sama.
- Jangan membagikan URL backend yang berisi token/rahasia jika backend Anda menggunakannya.

CARA HOSTING DAN INSTALASI
1. Unggah seluruh isi folder ini (bukan ZIP-nya) ke hosting statis HTTPS yang mendukung file service-worker.js pada direktori aplikasi, misalnya hosting statis yang Anda kelola.
2. Jangan hanya mengunggah index.html ke Blogger: service worker PWA umumnya harus berada pada origin dan scope yang sesuai; halaman Blogger tidak dapat begitu saja mendaftarkan service worker dari folder lain.
3. Buka URL HTTPS aplikasi di Chrome Android, lalu pilih menu browser “Install app” / “Tambahkan ke layar utama”.
4. Di iPhone, buka URL di Safari, pilih Share/Bagikan > Add to Home Screen/Tambahkan ke Layar Utama.
5. Izinkan kamera dan lokasi ketika diminta. Kamera dan geolocation memerlukan secure context (HTTPS atau localhost).

BATASAN OFFLINE
Paket ini memberi cache dasar untuk shell aplikasi, tetapi dependensi UI/QR/PDF/Excel masih dimuat dari CDN eksternal dan data tetap memakai backend Google Apps Script. Karena itu, jangan mengandalkan seluruh fungsi presensi berjalan offline. Presensi dan sinkronisasi data memerlukan koneksi internet.

PENGINGAT PRODUKSI
Service worker dan manifest membuat paket siap diuji sebagai PWA, bukan bukti bahwa backend telah lulus pengujian produksi. Tes pada Android dan iPhone sebelum digunakan untuk absensi resmi.
