# GDB + GEF Detail Guide
> GDB adalah debugger standar Linux, dan GEF (GDB Enhanced Features) membuatnya jauh lebih hebat untuk exploit dev.

## Perintah Penting GEF
- **`checksec`**: Melihat proteksi binary (Canary, NX, PIE, ASLR).
- **`vmmap`**: Melihat layout memori (mana yang RWX).
- **`pattern create 100`**: Membuat pattern unik untuk mencari offset crash.
- **`pattern search $rsp`**: Mencari offset setelah crash terjadi.
- **`registers`**: Melihat isi semua register (RAX, RBX, RIP, dll).
- **`heap chunks`**: Analisis heap memory (untuk tantangan pwn advanced).
- **`telescope`**: Melihat isi memori di sekitar alamat tertentu dengan cerdas.

## Workflow Debugging
1. `gdb ./program`
2. `break main` atau `break *0xaddress`
3. `run`
4. `next` (jalankan baris berikutnya) atau `step` (masuk ke dalam fungsi).
5. `x/10gx $rsp` (melihat 10 nilai di stack).
