# Kurikulum Offensive Security & Penetration Testing
> **Target:** GEMASTIK, CTF, Bug Bounty, & Professional Pentester.
> **Estimasi Waktu:** 6 Bulan (Intensif) - 2 Tahun (Mastery).

---

## Roadmap & Timeline Belajar

| Timeline | Fokus Utama | Target Milestone |
| :--- | :--- | :--- |
| **Bulan 1-2** | Fundamental & Linux Mastery | Menyelesaikan OverTheWire (Bandit) & THM Pre-Security. |
| **Bulan 3-4** | Recon & Web Hacking Basic | Menyelesaikan PortSwigger Academy (Apprentice) & PicoCTF. |
| **Bulan 5-6** | Network & Exploitation | Menyelesaikan THM Jr. Pentester & Root-Me (Web/Network). |
| **Tahun 1** | Advanced Web, PrivEsc, & CTF | Mencapai Rank Pro Hacker di HTB & Mengikuti GEMASTIK. |
| **Tahun 2** | Bug Bounty & Real Projects | Mendapatkan Bounty pertama & Sertifikasi (OSCP/eJPT). |

---

## Setup Virtual Lab (Wajib)
Sebelum memulai, siapkan "medan perang" Anda:
- [ ] Install **VMware Workstation** atau **VirtualBox**.
- [ ] Main OS: **Kali Linux** (Daily Driver/VM) atau **Parrot OS**.
- [ ] Target OS: **Metasploitable 2/3**, **Windows Server 2019** (eval).
- [ ] Browser Tools: Firefox dengan extension **FoxyProxy** dan **Wappalyzer**.

---

## PHASE 1: FUNDAMENTAL (Bulan 1-2)
*Jangan skip bagian ini. Tanpa pondasi, Anda hanya akan menjadi 'Script Kiddie'.*

### Linux & Kali Linux Mastery
- [ ] **[[Linux Filesystem Architecture]]** (bin, etc, var, home, tmp).
- [ ] **[[Command Line Mastery]]**: `ls`, `cd`, `grep`, `awk`, `sed`, `find`, `chmod`, `chown`.
- [ ] **[[Package Management]]**: `apt`, `dpkg`, source compilation.
- [ ] **[[Kali Linux Tools Overview]]**: Mengenal kategori tools di menu Kali.

### Networking fundamental
- [ ] **[[OSI Model & TCP-IP Stack]]**.
- [ ] **[[Protokol Jaringan Penting]]**: DNS, HTTP/HTTPS, SSH, FTP, SMB, SMTP, DHCP.
- [ ] **[[Subnetting & IP Addressing]]**.
- [ ] **[[Traffic Analysis Basics]]**: Dasar Wireshark & `tcpdump`.

### Automation & Scripting
- [ ] **Bash Scripting:** Loop, condition, variable, piping.
- [ ] **Python for Pentesters:** Request library, socket programming dasar, automation script.
- [ ] **Git & GitHub:** Clone, push, branch, managing tools.

---

## PHASE 2: RECON & ENUMERATION (Bulan 3)
*Hacking adalah 80% pengintaian, 20% eksekusi.*

### Passive & Active Recon
- [ ] **[[OSINT Methodology]]**: Google Dorking, Shodan, Censys, Whois lookup.
- [ ] **[[Subdomain Enumeration]]**: `amass`, `subfinder`, `assetfinder`.
- [ ] **[[Directory & File Fuzzing]]**: `ffuf`, `gobuster`, `dirsearch`.

### Service Enumeration
- [ ] **[[Nmap Mastery]]**: Scripting Engine (NSE), timing templates, evasion techniques.
- [ ] **[[Port Scanning Techniques]]**: TCP vs UDP scanning.
- [ ] **[[Fingerprinting & Banner Grabbing]]**.

---

## PHASE 3: WEB HACKING (Bulan 4-5)
*Fokus utama untuk Bug Bounty dan GEMASTIK.*

### Tools & Proxy
- [ ] **[[Burp Suite Mastery]]**: Repeater, Intruder, Decoder, Proxy, Extension.
- [ ] **[[HTTP Request Manipulation]]**: Headers, Cookies, Methods.

### OWASP Top 10 & Beyond
- [ ] **[[SQL Injection]]**: Manual (Union, Error, Blind) & `sqlmap`.
- [ ] **[[Cross-Site Scripting (XSS)]]**: Stored, Reflected, DOM-based.
- [ ] **[[Broken Access Control]]**: IDOR, Privilege Escalation.
- [ ] **[[SSRF (Server-Side Request Forgery)]]**.
- [ ] **[[XXE (XML External Entity)]]**.
- [ ] **[[SSTI (Server-Side Template Injection)]]**.
- [ ] **[[File Upload Vulnerability]]**: Bypass extension, RCE.
- [ ] **[[Authentication & Session Attacks]]**: JWT, OAuth, Hijacking.
- [ ] **[[API Hacking]]**: REST/GraphQL vulnerabilities.
- [ ] **[[Business Logic Vulnerabilities]]**: Race condition, Price manipulation.

---

## PHASE 4: NETWORK PENTEST & EXPLOITATION (Bulan 5-6)
*Fokus pada infrastruktur perusahaan dan internal network.*

### Network Attack
- [ ] **[[SMB Attacks]]**: Null session, `enum4linux`, SMB signing.
- [ ] **[[Brute Force Attacks]]**: `Hydra`, `Medusa` (SSH, FTP, RDP).
- [ ] **[[Responder & LLMNR Poisoning]]**.
- [ ] **[[Windows Domain Attacks]]**: CrackMapExec, Impacket basics.

### Exploitation Framework
- [ ] **[[Metasploit Framework Mastery]]**: msfconsole, msfvenom, meterpreter.
- [ ] **[[Reverse Shell vs Bind Shell]]**: Netcat, socat, pwncat.
- [ ] **[[Payload Delivery & Transfer]]**: Python server, certutil, wget.

---

## PHASE 5: PRIVILEGE ESCALATION (Advanced)
*Dari user biasa menjadi Root (Linux) atau SYSTEM (Windows).*

### Linux PrivEsc
- [ ] **[[Linux SUID-SGID Abuse]]**: GTFOBins.
- [ ] **[[Linux Cronjob Misconfig]]**: Writable scripts, PATH hijacking.
- [ ] **[[Linux Kernel Exploits]]**: DirtyPipe, DirtyCow.
- [ ] **[[Linux Sudoers Analysis]]**.

### Windows PrivEsc
- [ ] **[[Windows Token Manipulation]]**.
- [ ] **[[Windows Service Exploits]]**: Unquoted Service Path, Insecure Permissions.
- [ ] **[[Windows Registry Exploits]]**.
- [ ] **[[Windows Password Hunting]]**: Mimikatz, Config files.

---

## PHASE 6: SPECIALIZED TRACKS

### CTF & GEMASTIK Preparation
- [ ] **Cryptography:** RSA, AES, XOR, Caesar, Base64 (Dasar hingga Advanced).
- [ ] **Forensics:** Steganography, Memory Forensics (Volatility), Disk Image Analysis.
- [ ] **Reverse Engineering Dasar:** GDB, Ghidra, Cutter (Analyze binary flow).
- [ ] **Binary Exploitation (Pwn):** Buffer Overflow (Dasar), Stack Canary bypass.

### Bug Bounty Workflow
- [ ] **Hunting Methodology:** Memilih target (HackerOne/Bugcrowd).
- [ ] **Responsible Disclosure:** Cara melaporkan bug dengan benar.
- [ ] **CVSS Scoring:** Menentukan tingkat keparahan (Low, Medium, High, Critical).
- [ ] **Reporting:** Menulis laporan yang profesional dan reproducible.

---

## RESOURCE CENTER

### Platform Latihan (Wajib Ada)
1. **TryHackMe:** Terbaik untuk pemula (Terstruktur).
2. **Hack The Box:** Terbaik untuk praktik real-world (Competitive).
3. **PortSwigger Academy:** Kitab suci Web Hacking (Gratis & Sangat Bagus).
4. **PicoCTF:** Belajar dasar CTF untuk pemula.
5. **OverTheWire:** Belajar Linux via game (Bandit).
6. **VulnHub:** Download VM rentan untuk latihan offline.
7. **Root-Me:** Tantangan spesifik (Web, Network, Crypto).

### YouTube Channels
- **The Cyber Mentor:** Pentesting full course.
- **IppSec:** Walkthrough mesin HTB (Wajib tonton).
- **NahamSec / STOK:** Bug Bounty tips & live hunting.
- **LiveOverflow:** Deep dive technical security & CTF.
- **PwnFunction:** Visualisasi serangan web.

### Buku Rekomendasi
- *The Web Application Hacker's Handbook* (Dafydd Stuttard).
- *Black Hat Python* (Justin Seitz).
- *Linux Basics for Hackers* (OccupyTheWeb).
- *Penetration Testing: A Hands-On Introduction to Hacking* (Georgia Weidman).

---

## PORTFOLIO & PERSONAL BRANDING
*Cara agar dilirik perusahaan atau komunitas.*

### Membangun GitHub Cybersecurity
- [ ] Buat Repo **"CTF-Writeups"**: Simpan solusi challenge yang Anda selesaikan.
- [ ] Buat Repo **"Pentest-Tools"**: Kumpulan script automation buatan sendiri.
- [ ] Buat Repo **"Bug-Bounty-Methodology"**: Catatan checklist pribadi.

### Tips Menulis Writeup
- Fokus pada **"Why"** bukan hanya **"How"**.
- Jelaskan konsep vulnerability sebelum masuk ke exploit.
- Gunakan screenshot yang bersih dan poin-poin yang mudah dibaca.
- Publikasikan di Medium, Dev.to, atau Personal Blog.

---

## MILESTONE EVALUASI SKILL
- [ ] **Level 1:** Bisa mengoperasikan Linux tanpa GUI dan paham dasar networking.
- [ ] **Level 2:** Bisa melakukan scan Nmap dan menemukan directory tersembunyi.
- [ ] **Level 3:** Bisa mengeksploitasi SQL Injection manual di lab PortSwigger.
- [ ] **Level 4:** Bisa mendapatkan user shell di mesin Easy HackTheBox.
- [ ] **Level 5:** Bisa melakukan Privilege Escalation dan mendapatkan Root.
- [ ] **Level 6:** Mengikuti kompetisi CTF/GEMASTIK dan masuk Top 50.
- [ ] **Level 7:** Menemukan bug pertama di platform Bug Bounty.

---
> **"Hacking is a mindset, not just a set of tools. Stay curious and stay ethical."**
