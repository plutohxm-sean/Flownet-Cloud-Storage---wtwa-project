# FlowNet Storage - Cloud Storage Sederhana & Aman

**FlowNet** adalah aplikasi web cloud storage yang dibangun menggunakan HTML, CSS, PHP, Bootstrap, dan MySQL. Aplikasi ini memiliki fitur lengkap untuk upload, download, share file, serta keamanan dengan enkripsi dan verifikasi email.

## 📋 Fitur Utama

### ✅ Sesuai Requirement Proyek:

1. **Penggunaan HTML, PHP, dan Database** - ✓
2. **Penggunaan CSS** - ✓
3. **Penggunaan Framework Bootstrap** - ✓
4. **Penggunaan Table Relasi** - ✓ (users, files, shared_files, activity_log)
5. **Implementasi View Database** - ✓
6. **Implementasi Insert Database** - ✓
7. **Implementasi Update Database** - ✓
8. **Implementasi Delete Database** - ✓
9. **Hosting Website** - ✓ (siap di-hosting)
10. **Upload Foto** - ✓ (upload berbagai jenis file)
11. **Penggunaan Session Login** - ✓
12. **Penggunaan Session Logout** - ✓

### 🌟 Fitur Tambahan:

- **Enkripsi File dengan AES-256** 🔒
- **Verifikasi Email** ✉️
- **Reset Password via Email** 🔑
- **Share File ke User Lain** 👥
- **Log Aktivitas User** 📊
- **Dashboard yang Menarik** 🎨

## 🛠️ Teknologi yang Digunakan

- **Frontend**: HTML5, CSS3, Bootstrap 5, Bootstrap Icons
- **Backend**: PHP 7.4+
- **Database**: MySQL / MariaDB
- **Enkripsi**: OpenSSL (AES-256-CBC)
- **Email**: PHP Mail Function

## 📁 Struktur File

```
flownet/
├── config.php              # Konfigurasi database & fungsi umum
├── mailer.php             # Fungsi untuk mengirim email
├── index.php              # Landing page
├── register.php           # Halaman registrasi
├── login.php              # Halaman login
├── verify.php             # Verifikasi email
├── forgot_password.php    # Lupa password
├── reset_password.php     # Reset password
├── dashboard.php          # Dashboard utama
├── upload.php             # Proses upload file
├── download.php           # Proses download file
├── share.php              # Proses share file
├── delete.php             # Proses delete file
├── logout.php             # Proses logout
├── profile.php            # Halaman profile user (optional)
└── uploads/               # Folder untuk menyimpan file
```

## 🚀 Cara Instalasi

### 1. Setup Database

```sql
-- Buat database baru
CREATE DATABASE flownet_db;

-- Import struktur tabel dari file yang sudah disediakan
-- Atau jalankan SQL di database.sql
```

### 2. Konfigurasi File

Edit file `config.php`:

```php
// Konfigurasi Database
define('DB_HOST', 'localhost');
define('DB_USER', 'root');           // Sesuaikan
define('DB_PASS', '');               // Sesuaikan
define('DB_NAME', 'flownet_db');

// Konfigurasi Email (Gunakan Gmail SMTP)
define('SMTP_USER', 'your-email@gmail.com');
define('SMTP_PASS', 'your-app-password');
define('SMTP_FROM', 'your-email@gmail.com');

// Base URL
define('BASE_URL', 'http://localhost/flownet/');
```

### 3. Setup Folder Upload

```bash
# Buat folder uploads dan set permission
mkdir uploads
chmod 777 uploads
```

### 4. Konfigurasi Email Gmail

Untuk menggunakan fitur email verification:

1. Login ke Gmail Anda
2. Buka **Google Account Settings** → **Security**
3. Aktifkan **2-Step Verification**
4. Generate **App Password** untuk aplikasi
5. Gunakan App Password tersebut di `config.php`

### 5. Jalankan Aplikasi

```bash
# Menggunakan XAMPP/WAMPP
- Copy folder flownet ke htdocs
- Akses: http://localhost/flownet

# Atau menggunakan PHP Built-in Server
php -S localhost:8000
```

## 📖 Cara Penggunaan

### Registrasi User Baru

1. Buka halaman **Register**
2. Isi form: username, email, nama lengkap, password
3. Klik **Daftar Sekarang**
4. Cek email untuk verifikasi
5. Klik link verifikasi di email
6. Login dengan akun yang sudah diverifikasi

### Upload File

1. Login ke dashboard
2. Pilih file yang ingin diupload
3. **Optional**: Centang "Enkripsi File" untuk mengenkripsi
4. Klik tombol **Upload**

### Download File

1. Di dashboard, lihat daftar "File Saya"
2. Klik tombol **Download** pada file yang diinginkan
3. File akan terdownload (otomatis didekripsi jika terenkripsi)

### Share File

1. Klik tombol **Share** pada file
2. Masukkan username tujuan
3. Pilih apakah user boleh download atau hanya view
4. Klik **Share**
5. User tujuan akan menerima notifikasi email

### Delete File

1. Klik tombol **Delete** pada file
2. Konfirmasi penghapusan
3. File akan dihapus dari storage dan database

## 🔐 Keamanan

### Enkripsi File

FlowNet menggunakan **AES-256-CBC** untuk mengenkripsi file:

- Setiap file terenkripsi memiliki IV (Initialization Vector) unik
- Encryption key disimpan di database (terenkripsi)
- File hanya bisa dibaca setelah didekripsi

### Password Hashing

- Password user di-hash menggunakan **bcrypt**
- Tidak ada plain text password tersimpan di database

### Session Management

- Session timeout otomatis
- Session token unik per user
- Protection against session hijacking

## 📊 Database Schema

### Tabel: users
- `id` - Primary Key
- `username` - Unique
- `email` - Unique
- `password` - Hashed
- `full_name`
- `email_verified`
- `verification_token`
- `reset_token`
- `created_at`

### Tabel: files
- `id` - Primary Key
- `user_id` - Foreign Key → users
- `original_name`
- `stored_name`
- `file_path`
- `file_size`
- `encrypted`
- `encryption_key`
- `uploaded_at`

### Tabel: shared_files
- `id` - Primary Key
- `file_id` - Foreign Key → files
- `shared_by` - Foreign Key → users
- `shared_with` - Foreign Key → users
- `can_download`
- `shared_at`

### Tabel: activity_log
- `id` - Primary Key
- `user_id` - Foreign Key → users
- `action`
- `details`
- `ip_address`
- `created_at`

## 🎨 Tampilan

### Landing Page
- Hero section dengan gradient background
- Fitur unggulan dengan icon
- Statistics section
- Call-to-action button

### Dashboard
- Cards untuk statistik (Total File, Storage, Shared)
- Upload form dengan opsi enkripsi
- Tabs untuk "File Saya" dan "Dibagikan Ke Saya"
- File cards dengan action buttons (Download, Share, Delete)

### Authentication Pages
- Login page dengan gradient design
- Register page dengan form validation
- Forgot password dengan email verification
- Email verification page

## 🐛 Troubleshooting

### Email Tidak Terkirim

1. Pastikan SMTP credentials benar
2. Cek App Password Gmail sudah benar
3. Pastikan firewall tidak memblok SMTP port

### File Tidak Bisa Diupload

1. Cek permission folder `uploads/` (harus 777)
2. Cek `MAX_FILE_SIZE` di config.php
3. Cek `upload_max_filesize` di php.ini

### Error Database Connection

1. Pastikan MySQL/MariaDB sudah running
2. Cek credentials di config.php
3. Pastikan database sudah dibuat

## 📝 Catatan Penting

1. **Untuk Production**:
   - Ganti `ENCRYPTION_KEY` dengan key yang lebih aman
   - Gunakan HTTPS untuk koneksi aman
   - Set proper file permissions
   - Gunakan prepared statements (sudah implemented)

2. **Untuk Development**:
   - Error reporting sudah diaktifkan
   - Debug mode bisa diaktifkan di config.php

3. **Hosting**:
   - Aplikasi siap di-hosting di shared hosting
   - Pastikan PHP >= 7.4 dan MySQL >= 5.7
   - Upload semua file kecuali folder `uploads/` (buat manual)

## 👥 Tim Pengembang

Proyek ini dibuat untuk memenuhi tugas semester dengan requirement:
- HTML, PHP, Database ✓
- CSS & Bootstrap ✓
- CRUD Operations ✓
- Session Management ✓
- File Upload ✓
- Dan fitur-fitur tambahan

## 📄 Lisensi

Project ini dibuat untuk keperluan akademik/pembelajaran.

## 🙏 Credit

- Bootstrap 5
- Bootstrap Icons
- PHP OpenSSL untuk enkripsi

---

**FlowNet Storage** - Cloud Storage Sederhana, Aman & Terenkripsi! 🚀
