Berikut **contoh laporan lengkap** dengan **format persis seperti contoh yang Anda berikan**, tetapi berisi **HASIL SCAN dari laporan Anda (192.168.100.13)**.

Anda bisa **copy–paste langsung ke README atau laporan UAS**.

---

# 🔍 Laporan Hasil Scan Nmap – Metasploitable2

Repository ini berisi dokumentasi hasil scanning Nmap pada host **192.168.100.13**.

---

## 🖼️ Screenshot Hasil Scan

### 📌 Screenshot 1

<img src="gambar/metasploitable1.png" width="800">


---

### 📌 Screenshot 2

<img src="metasploitable2">

---

### 📌 Screenshot 3

<img src="metasploitable3">

---

---

# 📌 Command Nmap

```
nmap -n -Pn -p- -A 192.168.100.13 -o hasilscan.txt
```

---

# 📊 Tabel Hasil Scan Port

| Port | Status | Deskripsi                                                     |
| ---- | ------ | ------------------------------------------------------------- |
| 21   | open   | FTP – **ProFTPD 1.3.1**<br>• Anonymous login allowed          |
| 22   | open   | SSH – **OpenSSH 4.7p1 Debian 8ubuntu1**                       |
| 23   | open   | Telnet – Linux telnetd                                        |
| 25   | open   | SMTP – **Postfix smtpd**<br>• SSLv2 supported (rentan)        |
| 53   | open   | DNS – **ISC Bind 9.4.2**                                      |
| 80   | open   | HTTP – **Apache/2.2.8 (Ubuntu) DAV/2**<br>• Coyote JSP Engine |
| 111  | open   | rpcbind – RPC #100000                                         |
| 139  | open   | SMB – **Samba 3.0.20-Debian**                                 |
| 445  | open   | SMB – **Samba 3.0.20-Debian**<br>• SMBv1 (rentan)             |
| 512  | open   | exec – netkit-rsh rexec                                       |
| 513  | open   | login – rlogin (OpenBSD/Solaris)                              |
| 514  | open   | shell – tcpwrapped                                            |
| 1099 | open   | Java RMI – RMI registry (rentan RCE)                          |
| 1524 | open   | bindshell – Metasploitable backdoor                           |
| 2049 | open   | NFS – nfsd v2–4                                               |
| 2121 | open   | ProFTPD 1.3.1                                                 |
| 3306 | open   | MySQL 5.0.51a                                                 |
| 5432 | open   | PostgreSQL 8.3.x                                              |
| 5900 | open   | VNC – protocol 3.3                                            |
| 6000 | open   | X11 – access allowed                                          |
| 6667 | open   | UnrealIRCd – IRC (versi backdoor)                             |
| 7001 | open   | Apache JServ (AJP13)                                          |
| 8009 | open   | Apache JServ AJP13                                            |
| 8080 | open   | Apache Tomcat/Coyote JSP 1.1                                  |
| 8180 | open   | Apache Tomcat 5.5 Manager/Admin                               |

---

# 📘 Penjelasan Lengkap Hasil Scan Nmap

Berikut penjelasan tiap port berdasarkan hasil scan pada host **192.168.100.13**.

---

## 🔹 Port 21 – FTP (ProFTPD 1.3.1)

Server FTP mengizinkan **anonymous login**, sehingga siapapun bisa mengakses file tanpa autentikasi.
Versi 1.3.1 juga memiliki beberapa celah keamanan seperti buffer overflow.

---

## 🔹 Port 22 – SSH (OpenSSH 4.7p1)

Versi ini sudah sangat lama dan memiliki beberapa CVE terkait brute-force dan bypass autentikasi.

---

## 🔹 Port 23 – Telnet

Telnet berjalan tanpa enkripsi → data bisa disadap.
Tidak boleh digunakan pada sistem modern.

---

## 🔹 Port 25 – SMTP (Postfix)

SMTP mendukung SSLv2 yang sudah deprecated dan diketahui rentan.
Potensi serangan: email spoofing dan enum username.

---

## 🔹 Port 53 – DNS (Bind 9.4.2)

DNS server versi lama dengan banyak celah seperti:

* DNS poisoning
* Remote DoS
* Cache injection

---

## 🔹 Port 80 – HTTP (Apache 2.2.8)

Web server menjalankan versi Apache yang sangat tua.
Celah umum:

* RCE via WebDAV
* Directory traversal
* Multiple CVE pada mod_ssl

---

## 🔹 Port 111 – RPCBind

Digunakan untuk memetakan RPC service.
Jika dieksploitasi, dapat menjadi pintu serangan terhadap:

* NFS
* Rservices

---

## 🔹 Port 139 dan 445 – SMB (Samba 3.0.20)

SMBv1 terbuka sehingga:

* Rentan EternalBlue (MS17-010)
* Mendukung null session
* Signing disabled

---

## 🔹 Port 512 / 513 / 514 – Rservices

Layanan rexec, rlogin, dan rsh sangat tidak aman karena:

* Tidak terenkripsi
* Rentan hijacking
* Host-based trust mudah dipalsukan

---

## 🔹 Port 1099 – Java RMI Registry

Rentan terhadap **Remote Code Execution**.
Layanan ini umum dieksploitasi dalam lab pentest.

---

## 🔹 Port 1524 – Bindshell Backdoor

Port ini adalah **backdoor bawaan Metasploitable2**.
Memberikan akses root shell secara langsung.

---

## 🔹 Port 2049 – NFS

Jika export tidak dilindungi, penyerang bisa:

* Melakukan mount tanpa autentikasi
* Mengambil file sensitif
* Mengubah permission direktori

---

## 🔹 Port 2121 – ProFTPD

Versi lama yang memiliki celah RCE dan bypass autentikasi.

---

## 🔹 Port 3306 – MySQL

MySQL versi tua, sering memiliki:

* Default credential (root tanpa password)
* SQL injection pada beberapa tool bawaan

---

## 🔹 Port 5432 – PostgreSQL

Rawan brute-force dan exploitable pada versi ini.

---

## 🔹 Port 5900 – VNC

Menggunakan protokol lama tanpa enkripsi.
Password brute-force sangat mudah.

---

## 🔹 Port 6000 – X11

Dapat memungkinkan:

* Screenshot
* Keylogging
* Monitoring GUI

---

## 🔹 Port 6667 – UnrealIRCd (Backdoored)

Salah satu celah paling kritis di Metasploitable.
Versi ini **secara default berisi backdoor RCE**.

---

## 🔹 Port 7001 / 8009 – Apache JServ AJP13

Protokol lama yang sering digunakan untuk:

* File inclusion
* Upload webshell
* RCE pada Tomcat

---

## 🔹 Port 8180 – Apache Tomcat 5.5

Panel admin Tomcat bisa diakses dan sering memiliki:

* Password default
* Celah upload shell

---

# 📌 Ringkasan Tingkat Kerentanan

Host **192.168.100.13** sangat rentan karena:

* Banyak layanan lama tidak di-update
* Layanan tanpa autentikasi
* Password default
* Ada backdoor aktif
* Banyak port kritis terbuka

