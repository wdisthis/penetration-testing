# Essential Tools Mastery for Cyber Security
> File ini berisi daftar tools wajib dan contoh penggunaannya untuk kompetisi seperti GEMASTIK, CTF, dan real-world pentesting. Klik pada nama tool untuk melihat panduan penggunaan yang lebih rinci.

---

## Web Exploitation
*Fokus: Manipulasi HTTP, Fuzzing, dan Automation.*

- **[[tools-detail/Burp-Suite|Burp Suite]]**
  - *Fungsi:* Intercept dan modifikasi traffic HTTP.
  - *Contoh:* Aktifkan Proxy -> Intercept On -> Klik kanan "Send to Repeater" -> Ubah parameter input -> Klik "Send".
- **[[tools-detail/ffuf|ffuf]]**
  - *Fungsi:* Fuzzing direktori atau file dengan sangat cepat.
  - *Contoh:* `ffuf -u http://target.com/FUZZ -w /usr/share/wordlists/dirb/common.txt`
- **[[tools-detail/sqlmap|sqlmap]]**
  - *Fungsi:* Deteksi dan eksploitasi SQL Injection otomatis.
  - *Contoh:* `sqlmap -u "http://target.com/search.php?id=1" --dbs --batch`
- **[[tools-detail/Gobuster|Gobuster]]**
  - *Fungsi:* Enumerasi direktori atau DNS.
  - *Contoh:* `gobuster dir -u http://target.com -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt`
- **[[tools-detail/CyberChef|CyberChef]]**
  - *Fungsi:* Decoding/Encoding berbagai format (Base64, Hex, URL, dll).
  - *Contoh:* Masukkan string Base64 -> Pilih recipe "From Base64" -> Lihat outputnya.

---

## Reverse Engineering (RE)
*Fokus: Decompiling dan Static Analysis.*

- **[[tools-detail/Ghidra|Ghidra]]**
  - *Fungsi:* Decompiler file binary (ELF/EXE).
  - *Contoh:* Buka Ghidra -> New Project -> Import File -> Double click file -> Klik "Analyze" -> Lihat kode C di panel Decompiler.
- **[[tools-detail/JADX|JADX]]**
  - *Fungsi:* Decompile aplikasi Android (APK).
  - *Contoh:* `jadx-gui app.apk` -> Telusuri folder `sources` untuk membaca kode Java asli.
- **[[tools-detail/Strings|Strings]]**
  - *Fungsi:* Mencari teks yang bisa dibaca di dalam binary.
  - *Contoh:* `strings binary_file | grep "flag"`

---

## Binary Exploitation (Pwn)
*Fokus: Memory corruption dan exploit development.*

- **[[tools-detail/pwntools|pwntools]] (Python Library)**
  - *Fungsi:* Membuat script exploit secara profesional.
  - *Contoh:* `from pwn import *; io = remote('127.0.0.1', 1337); io.interactive()`
- **[[tools-detail/GDB-GEF|GDB + GEF]]**
  - *Fungsi:* Debugging binary saat dijalankan.
  - *Contoh:* `gdb ./program` -> `checksec` -> `pattern create 100` -> `run`.
- **[[tools-detail/Ropper|Ropper]]**
  - *Fungsi:* Mencari ROP gadgets.
  - *Contoh:* `ropper --file program --search "pop rdi"`

---

## Cryptography
*Fokus: Breaking ciphers dan matematis.*

- **[[tools-detail/Hashcat|Hashcat]]**
  - *Fungsi:* Cracking password hash tercepat (menggunakan GPU).
  - *Contoh:* `hashcat -m 0 hash.txt /usr/share/wordlists/rockyou.txt` (MD5 crack).
- **[[tools-detail/RsaCtfTool|RsaCtfTool]]**
  - *Fungsi:* Serangan otomatis pada kunci publik RSA yang lemah.
  - *Contoh:* `python3 RsaCtfTool.py --publickey key.pub --uncipher flag.enc`
- **[[tools-detail/SageMath|SageMath]]**
  - *Fungsi:* Perhitungan matematika tingkat tinggi (ECC, RSA, Lattice).
  - *Contoh:* Jalankan `sage` di terminal untuk menghitung `discrete_log`.

---

## Forensics & Network
*Fokus: PCAP analysis dan data extraction.*

- **[[tools-detail/Wireshark|Wireshark]]**
  - *Fungsi:* Analisis traffic jaringan secara visual.
  - *Contoh:* Buka file .pcap -> Filter `http` -> Klik kanan paket -> "Follow TCP Stream".
- **[[tools-detail/Volatility|Volatility]]**
  - *Fungsi:* Analisis memory dump (RAM).
  - *Contoh:* `vol -f mem.raw windows.info` -> `vol -f mem.raw windows.pslist`.
- **[[tools-detail/Binwalk|Binwalk]]**
  - *Fungsi:* Mengekstrak file tersembunyi di dalam file lain.
  - *Contoh:* `binwalk -e image.png` -> Periksa folder `_image.png.extracted`.
- **[[tools-detail/ExifTool|ExifTool]]**
  - *Fungsi:* Membaca metadata file (Gambar, PDF, dll).
  - *Contoh:* `exiftool suspicious.jpg | grep "GPS"`

---

## Tips Persiapan Gemastik
1. **Kuasai Nmap:** `nmap -sV -sC -T4 <IP>` adalah perintah pertama yang harus Anda jalankan.
2. **Siapkan Wordlist:** Selalu simpan `rockyou.txt` dan `directory-list-2.3` di folder tools Anda.
3. **Automasi:** Jika Anda melakukan hal yang sama lebih dari 3 kali, buatkan script Python-nya.

---
> **"Knowing the tool is 10%, knowing when and how to use it is 90%."**
