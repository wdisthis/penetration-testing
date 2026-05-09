# Binwalk Detail Guide
> Menganalisis dan mengekstrak file yang tertanam (embedded) di dalam file lain.

## Perintah Dasar
1. **Analisis Struktur File:**
   `binwalk file.png` (Akan menampilkan jika ada file ZIP atau JPEG di dalamnya).
2. **Ekstrak Otomatis:**
   `binwalk -e file.png` (Mengekstrak semua file yang ditemukan ke folder baru).
3. **Melihat Entropi:**
   `binwalk -E file.bin` (Grafik entropi tinggi menunjukkan data terenkripsi atau terkompresi).

## Kasus Steganography
Seringkali sebuah gambar terlihat normal, namun `binwalk` akan menemukan file `.zip` tersembunyi di "akhir" file gambar tersebut (Teknik appending).
 Riverside.
