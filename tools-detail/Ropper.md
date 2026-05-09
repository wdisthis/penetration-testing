# Ropper Detail Guide
> Mencari gadget ROP (Return Oriented Programming) di dalam binary.

## Perintah Dasar
```bash
ropper --file ./program --search "pop rdi"
```

## Kegunaan Utama
Saat binary memiliki proteksi **NX (No-eXecute)**, kita tidak bisa menjalankan shellcode di stack. Kita harus menggunakan potongan kode yang sudah ada di memori yang diakhiri dengan instruksi `ret`.

## Contoh Pencarian Gadget Umum
- `pop rdi; ret`: Untuk mengisi argumen pertama fungsi (x64).
- `pop rsi; pop rdx; ret`: Untuk mengisi argumen kedua dan ketiga.
- `syscall`: Untuk melakukan system call langsung.

## Tip
Jika binary terlalu kecil dan tidak punya banyak gadget, coba cari gadget di dalam **libc** yang digunakan program tersebut.
