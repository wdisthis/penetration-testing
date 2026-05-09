# Strings Detail Guide
> Utility sederhana namun sangat powerful untuk mencari teks yang bisa dibaca di dalam file binary.

## Perintah Dasar
```bash
strings nama_file
```

## Penggunaan di CTF
1. **Mencari Flag Langsung:**
   `strings challenge_file | grep "GEMASTIK{"`
2. **Melihat Fungsi yang Dipanggil:**
   `strings binary | grep "system"` (Indikasi celah keamanan jika ada pemanggilan system).
3. **Mencari Pesan Error:** Seringkali pesan error memberi petunjuk tentang alur logika program.

## Opsi Berguna
- `-n 10`: Hanya tampilkan string yang panjangnya minimal 10 karakter.
- `-e l`: Mencari string dengan encoding 16-bit (Little Endian), berguna untuk file Windows.
