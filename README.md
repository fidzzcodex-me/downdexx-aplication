# Downdexx Android

Aplikasi Android (Kotlin) yang membungkus situs Downdexx dan menambah fitur native: unduhan ke folder Downloads, menu Bagikan, halaman offline, dan splash dengan logo. Semua fitur situs ikut otomatis setiap kali situsnya di-deploy.

## Build lewat GitHub Actions

1. Buat repo baru dan push isi folder ini (workflow ada di `.github/workflows/android.yml`).
2. Di repo, buka Settings, Secrets and variables, Actions, tab Variables, lalu buat variable `SITE_URL` berisi alamat situs, misalnya `https://downdexx.vercel.app`.
3. Buka tab Actions, jalankan **Build APK** (otomatis berjalan saat push ke `main`).
4. Setelah selesai, unduh APK dari bagian Artifacts pada run tersebut.

APK debug langsung bisa dipasang. Untuk APK release yang bertanda tangan, tambahkan Secrets: `KEYSTORE_BASE64`, `KEYSTORE_PASSWORD`, `KEY_ALIAS`, `KEY_PASSWORD`.

## Build lokal

Buka folder ini di Android Studio, atau jalankan `gradle assembleDebug -PsiteUrl=https://domain-kamu`. Alamat situs juga bisa diubah di `gradle.properties`.

## Perilaku aplikasi

- Hanya halaman dari domain situs yang dibuka di dalam aplikasi. Tautan ke domain lain dibuka di browser.
- Tombol Unduh di situs memakai DownloadManager Android, jadi file masuk ke Downloads dengan notifikasi. Ini bekerja paling baik bila `PROXY_SECRET` sudah diisi di situs.
- Aplikasi muncul di menu Bagikan untuk teks. Link yang dibagikan dari TikTok, Instagram, YouTube, dan lainnya langsung diproses.
- Halaman Musik tetap memutar lagu saat layar dimatikan atau aplikasi di latar belakang. Android bisa menghentikannya bila memori sangat sempit.
- Butuh Android 10 atau lebih baru.

## Catatan distribusi

Bagikan sebagai APK langsung. Google Play melarang aplikasi yang memfasilitasi unduhan konten dari layanan seperti YouTube, jadi aplikasi ini kemungkinan besar ditolak di sana.
