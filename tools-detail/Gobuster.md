# Gobuster Detail Guide
> Tool untuk enumerasi direktori, subdomain, dan virtual host. Lebih stabil dibanding ffuf untuk koneksi lambat.

## Mode Penggunaan
1. **Directory Mode (dir):**
   `gobuster dir -u http://target.com -w /path/to/wordlist`
2. **DNS Mode (dns):**
   `gobuster dns -d target.com -w /path/to/subdomains.txt`
3. **VHOST Mode (vhost):**
   `gobuster vhost -u http://target.com -w /path/to/vhosts.txt`

## Opsi Berguna
- `-x php,txt,html`: Mencari file dengan ekstensi tertentu.
- `-k`: Abaikan verifikasi SSL/TLS (Sangat berguna untuk mesin lab HTB/THM).
- `-t 50`: Jumlah thread (Default 10, bisa dinaikkan untuk kecepatan).
- `-o output.txt`: Simpan hasil ke file.
