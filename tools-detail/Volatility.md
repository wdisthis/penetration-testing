# Volatility Detail Guide
> Standar industri untuk memory forensics (menganalisis RAM dump).

## Workflow Volatility 3
1. **Dapatkan Info OS:**
   `vol -f mem.raw windows.info`
2. **Lihat Daftar Proses yang Berjalan:**
   `vol -f mem.raw windows.pslist` (Lihat proses yang mencurigakan seperti `cmd.exe` atau `nc.exe`).
3. **Lihat Koneksi Network:**
   `vol -f mem.raw windows.netscan`
4. **Dump File dari Memori:**
   `vol -f mem.raw windows.dumpfiles --pid <PID>` (Misal untuk mengambil file yang baru saja dibuka oleh notepad).
5. **Cari Password/Hash:**
   `vol -f mem.raw windows.hashdump`

## Tip
Jika tantangannya adalah Linux, gunakan plugin `linux.pslist` (butuh profile yang sesuai).
