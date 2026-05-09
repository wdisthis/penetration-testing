# Ghidra Detail Guide
> Framework reverse engineering dari NSA yang sangat kompetitif.

## Workflow Dasar
1. **Create Project:** File -> New Project -> Non-Shared -> Beri nama.
2. **Import Binary:** File -> Import File -> Pilih file `.elf` (Linux) atau `.exe` (Windows).
3. **Analyze:** Double click file di list -> Jawab "Yes" saat ditanya untuk menganalisis -> Gunakan default options -> Analyze.
4. **Read Code:** Cari fungsi `main` di panel "Symbol Tree" -> Klik fungsi tersebut -> Baca kode C hasil decompiling di panel "Decompiler".

## Fitur Berguna
- **Rename Variables:** Tekan `L` pada variabel untuk mengganti namanya agar kode lebih mudah dibaca.
- **Set Data Type:** Tekan `T` untuk mengubah tipe data (misal dari `int` ke `char*`).
- **Function Graph:** Melihat alur logika program secara visual.
