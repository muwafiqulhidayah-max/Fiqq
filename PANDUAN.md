# Panduan Build APK — Muwafiq Dashboard

Project ini adalah aplikasi Android WebView yang membungkus file HTML kamu
(`app/src/main/assets/index.html`) supaya bisa dipasang sebagai aplikasi biasa di HP.

## Yang sudah disiapkan
- Data tetap tersimpan di **localStorage** di dalam app (aman, tidak hilang saat app ditutup)
- Fitur upload foto/video di form kegiatan & wishlist **sudah didukung** (kamera & galeri)
- Fitur sync ke Google Sheets tetap jalan asal HP terhubung internet
- Tombol back Android akan mundur di dalam app dulu, bukan langsung keluar

## Langkah build APK

1. **Install Android Studio** (gratis): https://developer.android.com/studio
2. Buka Android Studio → **Open** → pilih folder `MuwafiqApp` ini
3. Tunggu proses **Gradle Sync** selesai (butuh internet, otomatis download komponen yang perlu — bisa beberapa menit di percobaan pertama)
4. Sambungkan HP Android ke laptop (aktifkan **USB Debugging** di HP: Setelan → Tentang Ponsel → tekan "Nomor Build" 7x → muncul menu Developer Options → aktifkan USB Debugging)
5. Klik tombol **Run ▶** di Android Studio untuk langsung install & coba di HP, ATAU
6. Untuk ambil file APK: menu **Build → Build Bundle(s) / APK(s) → Build APK(s)**
7. Setelah selesai, klik notifikasi **"locate"** untuk membuka folder hasil APK
   (biasanya di `app/build/outputs/apk/debug/app-debug.apk`)
8. Kirim file `.apk` itu ke HP (lewat kabel/WA/Drive) lalu install seperti biasa
   (mungkin perlu izinkan "Install dari sumber tidak dikenal" di HP)

## Kalau mau ganti ikon aplikasi
Ganti isi file:
`app/src/main/res/mipmap/ic_launcher.xml`
Bisa juga generate ikon custom lewat **klik kanan folder `res` → New → Image Asset** di Android Studio.

## Kalau mau update isi aplikasi nanti
Cukup ganti file `app/src/main/assets/index.html` dengan versi HTML terbaru,
lalu build ulang APK (langkah 6-7 di atas).

## Catatan soal Google Apps Script (.gs)
File `.gs` kamu (backend sync ke Google Sheets) **tidak perlu dimasukkan ke Android** —
itu tetap jalan di Google Apps Script sebagai Web App terpisah. Aplikasi Android ini
hanya perlu URL Web App-nya (dimasukkan lewat pengaturan di dalam app, kolom "Sync Google Sheets").
