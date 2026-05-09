# ffuf Detail Guide
> Fast Fuzzing Utility written in Go. Sangat cepat untuk mencari file, direktori, atau subdomain.

## Perintah Dasar
```bash
ffuf -u http://target.com/FUZZ -w /path/to/wordlist.txt
```

## Opsi Penting
- `-u`: Target URL (Gunakan kata `FUZZ` sebagai placeholder).
- `-w`: Lokasi file wordlist.
- `-mc`: Match HTTP Status Code (contoh: `-mc 200,301`).
- `-fc`: Filter HTTP Status Code (contoh: `-fc 404`).
- `-fs`: Filter Size (sangat berguna untuk mengabaikan halaman error kustom).

## Contoh Skenario
1. **Mencari Direktori Tersembunyi:**
   `ffuf -u http://10.10.10.10/FUZZ -w /usr/share/wordlists/dirb/common.txt -mc 200`

2. **Fuzzing Extension File:**
   `ffuf -u http://10.10.10.10/indexFUZZ -w extensions.txt` (isi extensions.txt: `.php`, `.bak`, `.txt`).

3. **Subdomain Enumeration:**
   `ffuf -u http://FUZZ.target.com -w subdomains.txt`
