# Burp Suite Detail Guide
> Senjata utama untuk intercept dan manipulasi traffic HTTP.

## Fitur Utama
- **Proxy:** Menghentikan traffic sebelum sampai ke server/browser.
- **Repeater:** Mengirim ulang request yang sama dengan modifikasi berkali-kali.
- **Intruder:** Melakukan serangan brute-force atau fuzzing parameter.
- **Decoder:** Melakukan encoding/decoding cepat.

## Contoh Penggunaan Lanjutan
1. **Intercepting Traffic:**
   - Nyalakan "Intercept is ON" di tab Proxy.
   - Refresh halaman web di browser yang sudah dikonfigurasi.
   - Edit isi POST data atau Header (seperti User-Agent).
   - Klik "Forward".

2. **Bypassing Login via Repeater:**
   - Klik kanan pada login request -> "Send to Repeater".
   - Ubah `username=admin'--` dan `password=apapun`.
   - Klik "Send" dan lihat response-nya.

3. **Brute Force with Intruder:**
   - Kirim request ke Intruder.
   - Tandai parameter password dengan `§password§`.
   - Di tab Payloads, masukkan wordlist.
   - Klik "Start Attack".
