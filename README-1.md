# BOWOX STORE — Website Pembeli & Admin

Paket ini berisi **2 website** yang saling terhubung:

| File | Fungsi |
|---|---|
| `index.html` | Website untuk **PEMBELI** (pilih paket, order, isi saldo, kirim bukti transfer, terima link join) |
| `admin.html` | Website untuk **ADMIN** (ACC order, cek bukti transfer, kirim link join, ACC isi saldo) |
| `assets/qris.jpeg` | Gambar QRIS pembayaran (STR ARZ) yang tampil di website pembeli |

---

## Alur Sistem

1. Pembeli buka `index.html` → diminta **masukkan username** (tanpa akun/password lain).
2. Pembeli **pilih paket** → tekan **ORDER** → order masuk ke admin dengan status *MENUNGGU ACC*.
3. Admin buka `admin.html` → **Masuk** (atau **Buat Akun** jika admin baru) → tekan **ACC** (atau **TOLAK**).
4. Setelah di-ACC, pembeli **transfer ke QRIS** lalu tekan **KIRIM BUKTI** (upload screenshot).
5. Admin cek bukti → tekan **KIRIM LINK JOIN** → link langsung muncul di menu *Pesanan Saya* milik pembeli.
6. **Isi Saldo**: pembeli masukkan nominal → transfer QRIS → kirim bukti → admin tekan **ACC & TAMBAH SALDO** → saldo pembeli bertambah otomatis.

---

## Cara Deploy di GitHub Pages (Gratis)

1. Buat akun di [github.com](https://github.com) jika belum punya.
2. Klik **New repository** → beri nama misalnya `bowox-store` → pilih **Public** → **Create repository**.
3. Klik **uploading an existing file** → upload SEMUA isi folder ini (`index.html`, `admin.html`, folder `assets` beserta isinya) → **Commit changes**.
4. Masuk ke **Settings** → **Pages** → bagian *Branch* pilih **main** → **Save**.
5. Tunggu 1–2 menit, website aktif di:
   - Pembeli: `https://USERNAME.github.io/bowox-store/`
   - Admin: `https://USERNAME.github.io/bowox-store/admin.html`

## Login Admin

`admin.html` sekarang pakai sistem akun (username + password), bukan 1 password bersama:

- **Akun default**: username `bowox`, password `bowox2024` — langsung bisa dipakai, tidak perlu setting apa pun.
- **Buat Akun**: tiap admin bisa buat akun sendiri (username, email, password, ulangi password) lewat tab **BUAT AKUN** di halaman login, supaya tidak perlu berbagi 1 password yang sama.
- **Lupa Password**: klik "Lupa password?" di halaman login → masukkan username & email yang didaftarkan → buat password baru. Karena website ini tanpa server, resetnya lewat pencocokan username+email (bukan email asli yang terkirim).
- **Isi email untuk akun bowox**: akun default belum punya email. Login dulu → tab **AKUN SAYA** → isi email supaya fitur "Lupa Password" bisa dipakai untuk akun ini juga.
- Semua akun admin tersimpan di localStorage browser, sama seperti data order/saldo — lihat catatan di bawah.

---

## Catatan Penting

- Data order/saldo tersimpan di **browser (localStorage)**. Website pembeli dan admin **harus diakses dari domain & browser yang sama** agar datanya nyambung (contoh: admin dan pembeli sama-sama lewat link GitHub Pages Anda, dan admin tidak pakai mode incognito).
- File bukti transfer maksimal ±800KB (screenshot biasa cukup).
- Untuk reset semua data: buka browser → F12 → Console → ketik `localStorage.clear()` → Enter.
- Jika nanti ingin data tersimpan online lintas perangkat (HP pembeli ↔ laptop admin), perlu backend seperti Firebase — silakan minta dibuatkan versi Firebase.

© 2026 BOWOX STORE
