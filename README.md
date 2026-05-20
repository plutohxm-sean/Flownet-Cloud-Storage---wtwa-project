# FlowNet Storage

> Cloud Storage Sederhana, Aman, dan Terenkripsi menggunakan PHP & MySQL

FlowNet Storage adalah aplikasi web cloud storage berbasis **PHP Native** yang memungkinkan pengguna untuk mengunggah, mengunduh, membagikan, dan mengelola file secara aman.  
Aplikasi ini dilengkapi dengan fitur autentikasi, enkripsi file AES-256, verifikasi email, serta dashboard modern berbasis Bootstrap 5.

---

## Features

### Security Features
- AES-256 File Encryption
- Password Hashing menggunakan bcrypt
- Email Verification
- Password Reset via Email
- Session Authentication & Logout
- Activity Logging

### File Management
- Upload File
- Download File
- Delete File
- Share File antar User
- Shared File Access Control

### UI & User Experience
- Responsive Bootstrap 5 Interface
- Dashboard Statistik
- Modern Authentication Pages
- Clean File Management Layout

---

# Project Requirements Checklist

| Requirement | Status |
|---|---|
| HTML, PHP, Database | ✅ |
| CSS Styling | ✅ |
| Bootstrap Framework | ✅ |
| Relational Database Table | ✅ |
| Database View | ✅ |
| INSERT Query | ✅ |
| UPDATE Query | ✅ |
| DELETE Query | ✅ |
| Website Hosting Ready | ✅ |
| File Upload | ✅ |
| Login Session | ✅ |
| Logout Session | ✅ |

---

# Tech Stack

| Category | Technology |
|---|---|
| Frontend | HTML5, CSS3, Bootstrap 5 |
| Backend | PHP 7.4+ |
| Database | MySQL / MariaDB |
| Icons | Bootstrap Icons |
| Encryption | OpenSSL AES-256-CBC |
| Email Service | PHP Mail Function |

---

# Project Structure

```bash
flownet/
├── config.php
├── mailer.php
├── index.php
├── register.php
├── login.php
├── verify.php
├── forgot_password.php
├── reset_password.php
├── dashboard.php
├── upload.php
├── download.php
├── share.php
├── delete.php
├── logout.php
├── profile.php
└── uploads/
```

---

# Installation Guide

## 1. Clone Project

```bash
git clone https://github.com/yourusername/flownet-storage.git
cd flownet-storage
```

---

## 2. Create Database

```sql
CREATE DATABASE flownet_db;
```

Import file database:

```bash
database.sql
```

---

## 3. Configure Application

Edit file `config.php`

```php
define('DB_HOST', 'localhost');
define('DB_USER', 'root');
define('DB_PASS', '');
define('DB_NAME', 'flownet_db');

define('SMTP_USER', 'your-email@gmail.com');
define('SMTP_PASS', 'your-app-password');
define('SMTP_FROM', 'your-email@gmail.com');

define('BASE_URL', 'http://localhost/flownet/');
```

---

## 4. Create Upload Directory

```bash
mkdir uploads
chmod 777 uploads
```

---

## 5. Run Application

### Using XAMPP / Laragon

Move project folder into:

```bash
htdocs/
```

Open browser:

```bash
http://localhost/flownet
```

### Using PHP Built-in Server

```bash
php -S localhost:8000
```

---

# Gmail SMTP Configuration

Untuk menggunakan fitur email verification dan reset password:

1. Login ke akun Gmail
2. Buka:
   - Google Account
   - Security
3. Aktifkan:
   - 2-Step Verification
4. Generate:
   - App Password
5. Masukkan App Password ke `config.php`

---

# Usage Guide

## User Registration

1. Open Register Page
2. Fill registration form
3. Verify email address
4. Login using verified account

---

## Upload File

1. Login ke Dashboard
2. Select file
3. Optional:
   - Enable Encryption
4. Click Upload

---

## Download File

1. Open Dashboard
2. Select file
3. Click Download

Encrypted files akan otomatis didekripsi saat diunduh.

---

## Share File

1. Click Share Button
2. Input target username
3. Set permissions
4. Submit share request

---

## Delete File

1. Click Delete
2. Confirm action
3. File akan dihapus dari storage dan database

---

# Security Implementation

## AES-256 Encryption

FlowNet menggunakan:

- AES-256-CBC Encryption
- Unique Initialization Vector (IV)
- Secure Encryption Key Management

---

## Password Security

Password disimpan menggunakan:

```text
bcrypt hashing
```

Tidak ada password plain text yang disimpan di database.

---

## Session Management

Features:

- Secure Login Session
- Auto Session Timeout
- Session Hijacking Protection

---

# Database Schema

## users

| Column | Description |
|---|---|
| id | Primary Key |
| username | Unique Username |
| email | User Email |
| password | Hashed Password |
| full_name | Full Name |
| email_verified | Verification Status |

---

## files

| Column | Description |
|---|---|
| id | Primary Key |
| user_id | Foreign Key |
| original_name | Original File Name |
| stored_name | Stored File Name |
| encrypted | Encryption Status |

---

## shared_files

| Column | Description |
|---|---|
| id | Primary Key |
| file_id | Shared File ID |
| shared_by | Sender User |
| shared_with | Receiver User |

---

## activity_log

| Column | Description |
|---|---|
| id | Primary Key |
| user_id | User ID |
| action | Activity Action |
| ip_address | User IP |

---

# User Interface

## Landing Page
- Hero Section
- Gradient Background
- Feature Showcase
- Call To Action Button

## Dashboard
- Statistics Cards
- Upload Form
- File Management Tabs
- Action Buttons

## Authentication Pages
- Login Page
- Register Page
- Forgot Password
- Email Verification

---

# Troubleshooting

## Email Not Sending

- Verify SMTP credentials
- Check Gmail App Password
- Ensure SMTP port is not blocked

---

## Upload Failed

Check:

```bash
upload_max_filesize
post_max_size
```

in `php.ini`

Also ensure:

```bash
chmod 777 uploads
```

---

## Database Connection Error

Ensure:

- MySQL/MariaDB is running
- Database exists
- Credentials are correct

---

# Deployment Notes

## Production Recommendations

- Use HTTPS
- Change default encryption key
- Set secure file permissions
- Disable debug mode

---

## Server Requirements

| Requirement | Version |
|---|---|
| PHP | >= 7.4 |
| MySQL | >= 5.7 |
| Apache/Nginx | Latest |

---

# Developer

Developed for academic and learning purposes.

---

# License

This project is intended for educational purposes only.

---

# Credits

- Bootstrap 5
- Bootstrap Icons
- PHP OpenSSL

---

# FlowNet Storage

> Secure • Simple • Encrypted Cloud Storage Solution
