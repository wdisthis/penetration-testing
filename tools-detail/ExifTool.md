# ExifTool Detail Guide
> Membaca, menulis, dan mengedit metadata dalam berbagai jenis file.

## Kegunaan di CTF
1. **Mencari Flag di Metadata:**
   `exiftool image.jpg | grep -i "flag"`
2. **Mengecek Lokasi GPS:**
   Seringkali tantangan OSINT menyembunyikan koordinat GPS di metadata foto.
3. **Melihat Software Pembuat:**
   Informasi seperti "Photoshop" atau "GIMP" bisa memberi petunjuk apakah file telah dimodifikasi.
4. **Melihat Waktu Pembuatan:**
   `File Modification Date/Time` bisa membantu menyusun timeline kejadian dalam forensik.

## Tip
Jika Anda ingin membersihkan metadata file Anda sendiri sebelum mengunggahnya ke internet, gunakan:
`exiftool -all= image.jpg`
 Riverside.
