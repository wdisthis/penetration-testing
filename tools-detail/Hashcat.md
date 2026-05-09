# Hashcat Detail Guide
> Advanced Password Recovery. Tool tercepat untuk cracking hash menggunakan daya komputasi GPU.

## Mode Hash yang Sering Dipakai
- `-m 0`: MD5
- `-m 100`: SHA1
- `-m 1400`: SHA256
- `-m 1800`: SHA512
- `-m 400`: Wordpress (MD5)

## Contoh Serangan
1. **Dictionary Attack (Paling Umum):**
   `hashcat -m 0 hash.txt /usr/share/wordlists/rockyou.txt`
2. **Brute Force (Mask Attack):**
   `hashcat -m 0 hash.txt -a 3 ?l?l?l?l` (Mencoba semua kombinasi 4 huruf kecil).
3. **Hybrid Attack:**
   `hashcat -m 0 hash.txt rockyou.txt -a 6 ?d?d` (Wordlist + 2 angka di belakang).

## Tip
Gunakan `--show` untuk melihat hasil crack yang sudah pernah dilakukan sebelumnya tanpa menjalankan proses cracking lagi.
