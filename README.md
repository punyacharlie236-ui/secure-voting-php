# 🗳️ Secure Online Voting System (PHP Native & MySQL)

A lightweight, responsive, and security-hardened web-based voting application built with Native PHP 8 and MySQL. This project demonstrates backend coding best practices, defensive programming, anti-fraud tracking, and mitigation of common web application vulnerabilities (OWASP Top 10).

---

## ✨ Key Features & Security Implementation

### 1. 🛡️ Anti-Fraud Mechanism
* **Session ID & IP Tracking:** Mencegah pemberian suara ganda (*double voting*) dengan memeriksa kombinasi `session_id()` dan `$_SERVER['REMOTE_ADDR']`.
* **State Verification:** Antarmuka pemilih dinonaktifkan secara otomatis jika identitas sesi/IP terdeteksi telah menggunakan hak suara.

### 2. 🔒 Security Hardening
* **SQL Injection Prevention:** 100% interaksi database yang dinamis menggunakan Parameterized Prepared Statements (`mysqli_stmt`).
* **CSRF Mitigation:** Verifikasi token *Cross-Site Request Forgery* berbasis kriptografi acak (`random_bytes(32)`) pada setiap request `POST`.
* **XSS Defense:** Sanitasi output otomatis menggunakan `htmlspecialchars()` dengan flag `ENT_QUOTES` dan encoding `UTF-8`.
* **Hardened Session Cookies:** Konfigurasi cookie dengan atribut `HttpOnly`, `SameSite=Lax`, dan `Secure` (jika HTTPS aktif).

### 3. 📊 Real-Time Live Dashboard
* **AJAX Polling:** Dashboard pemantauan (`hasil.php`) melakukan pembaruan persentase dan grafik progress bar secara asinkron setiap 5 detik via JavaScript Fetch API ke endpoint `get_hasil.php`.
* **DOM-XSS Safe:** Rendering elemen antarmuka menggunakan manipulasi `textContent` dan sanitasi DOM.

### 4. ⚙️ Protected Admin Panel
* **Session-Authenticated Dashboard:** Mengelola data kandidat dan pemantauan suara dengan proteksi login admin (`admin.php`).
* **Safe Mutating Operations:** Tambah kandidat, hapus kandidat (dengan validasi relasi suara), dan reset data (*TRUNCATE*) terproteksi CSRF.

---

## 📁 Project Structure

```text
├── config.php                # Konfigurasi database, helper CSRF, & sanitasi XSS
├── database.sql              # Skema tabel MySQL (kandidat & vote)
├── index.php                 # Halaman utama & form pemilihan suara
├── proses_vote.php           # Backend handler & validasi integritas vote
├── hasil.php                 # Dashboard antarmuka grafik hasil live voting
├── get_hasil.php             # Endpoint REST API JSON untuk agregasi suara
├── admin.php                 # Panel kontrol administrasi terproteksi
└── README.md                 # Dokumentasi proyek
