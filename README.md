<div align="center">

# 🗳️ Secure Online Voting System
### PHP 8.x • MySQL Security Hardened • Real-Time Architecture

[![PHP Version](https://img.shields.io/badge/PHP-8.0%2B-777BB4?style=for-the-badge&logo=php&logoColor=white)](https://php.net)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://mysql.com)
[![Security](https://img.shields.io/badge/Security-OWASP_Hardened-10B981?style=for-the-badge&logo=auth0&logoColor=white)](#-security-hardening-architecture)
[![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](LICENSE)

<p align="center">
  A lightweight, responsive, and defensive web-based voting application with anti-fraud tracking, parameterized SQL statements, CSRF protection, and asynchronous real-time polling.
</p>

</div>

---

## 🏛️ Live Runtime Architecture Map

<!-- ARCHIFY ANIMATED RUNTIME MAP -->
<div align="center">
  <img src="./assets/architecture.svg" alt="Secure Voting System Architecture Map" width="100%">
</div>

<br>

| 🛡️ Guided Story: Anti-Fraud | 🔍 Route Probe: Live Stream | 🔬 Security Lens: Admin Gate |
| :--- | :--- | :--- |
| **Pencegahan Double Vote**<br>Memverifikasi `session_id()` dan `$_SERVER['REMOTE_ADDR']` untuk memblokir voting berulang sebelum data disimpan ke database. | **Real-Time Agregasi 5s**<br>JavaScript Fetch API melakukan polling asinkron ke `get_hasil.php` tanpa perlu me-reload seluruh halaman browser. | **Proteksi Akses Penuh**<br>Operasi mutasi data (Tambah, Hapus, Truncate) diproteksi autentikasi sesi admin dan verifikasi token CSRF. |

---

## 🔒 Security Hardening Architecture
