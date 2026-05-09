# Wireshark Detail Guide
> Analisis traffic jaringan (PCAP) secara visual dan mendalam.

## Shortcut & Tips
- **`http`**: Filter hanya traffic web.
- **`ip.addr == 10.10.10.10`**: Filter berdasarkan IP.
- **`tcp.port == 4444`**: Filter berdasarkan port tertentu (sering digunakan untuk shell).
- **`frame contains "flag"`**: Mencari teks "flag" di seluruh paket.

## Workflow Analisis
1. **Follow TCP Stream:** Klik kanan pada paket -> Follow -> TCP Stream. Ini akan menyatukan seluruh percakapan antara client dan server dalam teks yang bisa dibaca.
2. **Export Objects:** File -> Export Objects -> HTTP. Berguna untuk mengambil file (gambar, script, dokumen) yang di-download oleh target saat perekaman traffic berlangsung.
3. **Statistics -> Protocol Hierarchy:** Melihat distribusi protokol (misal: 90% traffic adalah DNS, indikasi DNS Tunneling).
