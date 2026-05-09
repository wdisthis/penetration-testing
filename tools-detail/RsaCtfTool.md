# RsaCtfTool Detail Guide
> Serangan otomatis pada kunci publik RSA yang lemah. Tool wajib untuk tantangan Cryptography di CTF.

## Cara Penggunaan
1. **Diberikan Public Key dan Ciphertext:**
   `python3 RsaCtfTool.py --publickey key.pub --uncipher flag.enc`
2. **Diberikan Public Key saja (untuk mencari Private Key):**
   `python3 RsaCtfTool.py --publickey key.pub --private`
3. **Mencari Flag dari beberapa Public Key yang menggunakan N yang sama:**
   `python3 RsaCtfTool.py --key key1.pub key2.pub --attack common_modulus`

## Jenis Serangan yang Didukung
- Wiener's attack
- Hastad's attack (Low exponent)
- Fermat's factorization
- Boneh Durfee
- Dan banyak lagi secara otomatis.
