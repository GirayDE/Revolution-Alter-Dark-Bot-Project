# AlterBot (ADB) Suite — Release v4.2.878

> **Status Rilis**: SUKSES & SIAP DIGUNAKAN
> **Waktu Build**: Sabtu, 14 November 2026 pukul 11:30:52 WIB
> **Target FLA**: `LoadBOTv2.fla`
> **Target SWF**: `ADBLoader.swf`

---

## 1. Catatan Pembaruan (Changelog)

Build Android Puffin/Ruffle (basis ADB 3.9) & iOS menggunakan ADBLoader.swf langsung, dengan nama aplikasi AlterBot ver.4.2.

---

## 2. Sinkronisasi Versi Lintas Platform

Mode Sinkronisasi: **TERKUNCI (Semua Platform Mengikuti Master v4.2.878)**

| Platform | Versi Aktif | Metadata Internal yang Disinkronkan |
| :--- | :--- | :--- |
| **SWF / ActionScript 3** | `v4.2.878` | `MainTimeline.CURRENT_BOT_VERSION = "4.2.878"` |
| **Android Puffin/Ruffle (.apk)** | `v4.2.878` | `versionName="4.2.878"`, `versionCode=4020878` |
| **iOS Native (.ipa)** | `v4.2.878` | `CFBundleShortVersionString="4.2.878"` |

---

## 3. Status Script ActionScript 3 (Pembaruan Kode)

- **Semua skrip ActionScript 3 (167+ modul) dalam kondisi sinkron dan up-to-date** dengan SWF rilis.
- Tidak ada perubahan file `.as` baru sejak kompilasi terakhir.

---

## 4. Artefak Distribusi & Checksum SHA-256

Daftar file biner dan paket yang dihasilkan pada rilis ini:

| Nama File | Platform / Format | Ukuran | Checksum SHA-256 |
| :--- | :--- | :--- | :--- |
| `ADBLoader.swf` | Shockwave Flash Biner (AVM2) | 1.38 MB | `a8588ec69efc6560cb510fd9b03b9e7e27b33b2f2d989d3a66bff93042aa66b5` |
| `AlterBot ver.4.2 (Ruffles).apk` | Android Mobile (Puffin / Ruffle WASM, 16KB Page-Aligned) | 55.50 MB | `b68ab18a6fb6d5f9c2d6ca0315e5828e07ad3108daa1d87caa4b008e6342060d` |
| `AlterBot ver.4.2 (iOS).ipa` | iOS Native App (Payload Bundle) | 22.87 MB | `b2e2fc2dee298c2c226d8d6874fcf676e0611f395a1d277e412e62a3395530d6` |
| `version.json` | Manifest Metadata Rilis | 753 B | `45698e93d578b268ecb3882c4012daf0427c6601ee403821aeb8d9b5b359f935` |

---

## 5. Panduan Penggunaan & Instalasi

### Windows PC Desktop
1. Ekstrak file `.zip` / `.7z` atau buka langsung file `.exe` rilis.
2. Bot menggunakan internal Flash Player Standalone Anti-Freeze yang dioptimalkan.
3. Tidak memerlukan instalasi Adobe Animate atau Flash Player eksternal.

### Android (Puffin / Ruffle Mobile)
1. Pasang file `.apk` pada perangkat Android (mendukung Android versi 10 hingga Android 16).
2. Native library sudah 16 KB page-aligned dan ditandatangani skema v1, v2, serta v3.
3. Dilengkapi ikon kustom ADB (ikon legacy, round, dan adaptive foreground).

### iOS / iPadOS
1. Instal file `.ipa` menggunakan sideload tool seperti Sideloadly, AltStore, TrollStore, atau Scarlet.
2. Pastikan profil developer dipercayai pada menu *Settings > General > VPN & Device Management*.

### Safari Web PWA
1. Ekstrak bundle zip atau 7z Safari-PWA ke folder lokal.
2. Buka `index.html` pada browser Chrome, Safari, Edge, atau Firefox untuk memainkan secara offline dengan engine Ruffle WASM.

---
*Dokumentasi ini dibuat otomatis oleh AlterDarkBot Builder Studio v2.0 pada Sabtu, 14 November 2026 pukul 11:30:52 WIB*
