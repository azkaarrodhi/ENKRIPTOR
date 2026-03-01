# 🔐 ENKRIPTOR

> Secure, client-side file encryption directly in your browser.  
> No server. No upload. No tracking.

ENKRIPTOR adalah aplikasi enkripsi file berbasis web yang memungkinkan pengguna mengenkripsi dan mendekripsi **semua jenis file** langsung di browser menggunakan **Argon2id** dan **AES-GCM 256-bit**.

Semua proses kriptografi dilakukan sepenuhnya di sisi klien (client-side).

---

## ✨ Features

- 🔐 AES-GCM 256-bit encryption
- 🧠 Argon2id key derivation (memory-hard)
- 📁 Mendukung semua format file
- 📷 QR Code untuk master password (kamera & gambar)
- 🔒 Auto-lock setelah 2 menit tidak aktif
- 🌐 100% client-side (tanpa server)
- 🧾 Struktur file terenkripsi menyimpan metadata nama file asli

---

## 🛡️ Security Model

### Key Derivation

Menggunakan **Argon2id** dengan parameter:

| Parameter      | Value |
|---------------|--------|
| Time Cost     | 3      |
| Memory        | 64 MB  |
| Parallelism   | 1      |
| Output Length | 32 bytes (256-bit) |

### Encryption

- Algorithm: AES-GCM
- IV: 12 bytes (random)
- Salt: 16 bytes (random per file)
- Authenticated encryption (integrity protected)

### `.secret` File Format

```
[ 16 bytes salt ]
[ 12 bytes IV ]
[ 2 bytes filename length (Uint16 LE) ]
[ original filename ]
[ encrypted file data ]
```

---

## 🚀 Getting Started

### Option 1 — Open Directly

1. Download repository
2. Open `index.html` in your browser

### Option 2 — Run Local Server (Recommended)

```bash
npx serve
```

---

## 📖 Usage

### 🔓 Open Existing Encrypted File

1. Masukkan master password.
2. Pilih file `.secret`.
3. Klik **Buka / Buat File Enkripsi**.
4. Jika password benar, file bisa diunduh dalam format asli.

### 🆕 Create New Encrypted File

1. Masukkan master password.
2. Klik **Buka / Buat File Enkripsi** (tanpa memilih file).
3. Tambahkan file.
4. Klik **Simpan & Enkripsi**.
5. File `.secret` akan otomatis terunduh.

### 📷 Use QR Code for Password

- Scan via camera
- Upload QR image
- Password otomatis terisi

---

## ⚠️ Important Warning

- Jika master password hilang → file **tidak dapat dipulihkan**
- Tidak ada reset password
- Tidak ada backdoor
- Tidak ada recovery mechanism

Gunakan passphrase panjang dan unik.

---

## 🔒 Privacy

✔ No server  
✔ No cloud storage  
✔ No analytics  
✔ No telemetry  
✔ No data leaves your device  

---

## 🧰 Tech Stack

- HTML5
- CSS3
- Vanilla JavaScript
- Web Crypto API
- Argon2 (browser implementation)
- QR Scanner Library
- SweetAlert2

---

## 📌 Threat Model

ENKRIPTOR melindungi terhadap:

- Pencurian file statis
- Akses tidak sah ke file terenkripsi
- Modifikasi file (integrity via AES-GCM)

ENKRIPTOR **tidak** melindungi terhadap:

- Keylogger di perangkat
- Malware
- Shoulder surfing
- Password lemah

Keamanan sepenuhnya bergantung pada kekuatan master password.

---

## 🧪 Security Notes

- Salt unik untuk setiap file
- IV unik untuk setiap enkripsi
- Tidak menyimpan password di memori permanen
- Auto reload setelah 2 menit idle

---

## 📄 License

This project is released under the Creative Commons CC0 1.0 Universal License.

However, this project includes third-party libraries that are licensed under their own licenses (e.g., MIT License).
See their respective license files for details.
You are free to:

- Copy
- Modify
- Distribute
- Use commercially
- Use privately




