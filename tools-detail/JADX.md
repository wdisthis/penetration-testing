# JADX Detail Guide
> Dex to Java decompiler. Tool wajib untuk membedah aplikasi Android (APK).

## Cara Penggunaan
1. **GUI Mode:** Jalankan `jadx-gui` dan buka file `.apk`.
2. **CLI Mode:** `jadx file.apk -d out_dir` (Akan mengekstrak semua kode ke folder `out_dir`).

## Hal yang Harus Dicari di APK
- **strings.xml:** Seringkali berisi API Key, Firebase URL, atau hardcoded credentials.
- **AndroidManifest.xml:** Melihat activity yang diekspor (bisa diakses tanpa login) dan permission aplikasi.
- **Certificate:** Mengecek tanda tangan aplikasi.
- **Native Libraries:** Folder `lib/` yang berisi file `.so` (butuh Ghidra untuk membacanya).
