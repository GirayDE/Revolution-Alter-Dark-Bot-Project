# ⚔️ AlterDarkBot (ADB) — AQW Cross-Platform Bot Client

[![Version](https://img.shields.io/badge/Version-v4.1-blue.svg?style=flat-square)](https://github.com)
[![Platform](https://img.shields.io/badge/Platform-Android%20%7C%20iOS%20%7C%20Windows%20%7C%20macOS-success.svg?style=flat-square)](https://github.com)
[![Engine](https://img.shields.io/badge/Engine-Flash%20%2F%20Ruffle%20WASM%20%2F%20Harman%20AIR-orange.svg?style=flat-square)](https://github.com)
[![Architecture](https://img.shields.io/badge/Android-16KB%20Page--Aligned%20(ARM32%2F64)-purple.svg?style=flat-square)](https://github.com)

**AlterDarkBot (ADB)** adalah bot client serbaguna dan multi-platform untuk *AdventureQuest Worlds* (AQW). Dirancang dengan arsitektur modern berbasis Flash, Ruffle WebAssembly, dan Harman AIR, ADB memungkinkan kamu menjalankan otomasi farming, questing, dan combat secara efisien baik di perangkat PC maupun perangkat mobile (Android & iOS).

---

## 🌟 Fitur Unggulan

### ⚔️ 1. Combat & Monster Management
- **Targeting Fleksibel**: Serang monster spesifik berdasarkan nama atau gunakan mode acak (*Kill Random*).
- **Hunt for Drops**: Otomatis farming monster hingga target item (Regular maupun Temporary) terpenuhi dengan batas jumlah (*Quantity*).
- **Custom Skill Sequence**: Atur urutan skill dan cooldown sesuai class yang kamu pakai.
- **Smart AI Skill**: Mode adaptif cerdas untuk eksekusi skill otomatis.
- **Auto Rest & Safe Recovery**: Mengatur batas HP/MP untuk istirahat otomatis di luar combat.
- **Goto Player**: Otomatis berpindah (*goto*) ke pemain lain dalam room.

### 🎒 2. Smart Drops & Item Manager
- **Filter Drop Komprehensif**:
  - *Pickup All Drops* / *Pickup Whitelist Only*
  - *Pickup AC-Tagged Items* (aman untuk item berharga/rare)
  - *Decline All Drops* & *Reject Non-Whitelist*
- **Item Whitelist Manager**: Tambah, hapus, simpan, dan muat daftar whitelist drop favorit kamu.
- **Conditional Item Statements**: Logika percabangan bot berdasarkan keberadaan item atau jumlahnya di inventory/bank.
- **Shop Loader & Fast Buy**: Buka shop ID manapun dari jarak jauh dan beli item secara instan (*Fast Buy*).
- **Map Item Automation**: Ambil item interaktif map secara otomatis.

### 🗺️ 3. Map & Movement Control
- **Cell & Pad Navigation**: Lompat ke Cell dan Pad tertentu dengan mudah (*Grab & Add Cell*).
- **Coordinate Walker**: Ambil koordinat X/Y dan arahkan karakter berjalan ke titik presisi.
- **Private Room Automation**: Fitur otomatis masuk ke room privat (cth: `/join battleon-999999`).
- **Map Statements**: Validasi posisi map/room sebelum menjalankan instruksi berikutnya.
- **Custom Delay**: Pengaturan jeda waktu transisi room untuk menghindari lag atau disconnections.

### 📜 4. Quest Automation
- **Multi-Quest Support**: Load dan jalankan beberapa Quest ID secara simultan.
- **Auto Accept & Complete**: Menerima dan menyelesaikan quest otomatis saat syarat terpenuhi.
- **Quest Item Whitelist**: Ambil daftar item persyaratan (*Requirements*) atau hadiah (*Rewards*) quest langsung ke whitelist dengan satu klik.

### 🧠 5. Logic Scripting & Control (Misc)
- **Label & Goto System**: Struktur percabangan skrip yang rapi menggunakan penanda *Label* dan lompatan baris (*Goto Label*).
- **General Statements**: Kondisi logika berbasis event, status player, dan status game.
- **Packet Tools**: Fitur *Packet Spammer* dan pengiriman custom packet langsung ke server.
- **Audio Alarm**: Notifikasi suara saat item tertentu berhasil didapatkan.
- **Execution Flow Controls**: Perintah `Stop`, `Restart`, `Logout`, dan `Return`.

### 🛡️ 6. Safety & Client Options
- **Anti-Ban Protections**:
  - *Exit Combat Before Complete Quest*
  - *Exit Combat Before Rest*
  - *Wait for Skill Cooldown*
  - *Exit Combat On Stop / On Join*
- **Anonymous Name**: Menyembunyikan nama karakter di layar untuk keamanan screenshot/recording.
- **Client Spoofing (Visual Only)**:
  - Ganti Alignment (*Good, Evil, Chaos, Undecided*).
  - Ubah tampilan Username, Guild, Level, dan Class di sisi client.
  - Simulasi hak akses *Member* atau *Moderator*.
  - Sembunyikan layar loading (*Hide Loading Screen*) dan *Reload Current Map*.

### 📂 7. Integrated Bot Manager & Storage Bridge
- **Directory Tree Bot List**: Navigasi bot bersarang (*nested folders*) dengan pratinjau instan untuk *Author* dan *Deskripsi*.
- **Storage Bridge Mobile**: Integrasi penuh dengan sistem file Android (Storage Access Framework) & iOS untuk Load/Save skrip bot langsung dari memori perangkat.

---

## 📱 Dukungan Lintas Platform (Cross-Platform)

| Platform | Format File | Kompatibilitas | Mesin Utama |
| :--- | :--- | :--- | :--- |
| **Android** | `.apk` | Android 10 s/d 16 | 16 KB Page-Aligned (ARM32 / ARM64), Ruffle / Harman AIR |
| **iOS / iPadOS** | `.ipa` / `.mobileconfig` | iOS 12.0 s/d 18+ | Native IPA (Sideload) & Safari PWA WebAssembly |
| **Windows** | `.exe` | Windows 7 / 8 / 10 / 11 | Anti-Freeze Flash Engine Standalone |
| **macOS** | `.app` / `.zip` | macOS Catalina s/d Sequoia | Native Mac Wrapper Bundle |

---

## 🚀 Panduan Instalasi & Penggunaan

### 🤖 1. Android
File: `ADB 4.1 (Ruffles).apk` atau `ADB Ver.3.0 (ARM64).apk`
- **16 KB Page-Aligned**: Kompatibel penuh dan dioptimalkan untuk Android versi terbaru (Android 10 hingga Android 16).
- **Tanda Tangan Digital**: Ditandatangani dengan skema signature v2 & v3 (`apksigner`).
- **Instalasi**:
  1. Unduh file `.apk` ke ponsel Android kamu.
  2. Buka file manager dan izinkan instalasi dari *Unknown Sources* (Sumber Tidak Dikenal).
  3. Buka aplikasi ADB, berikan izin akses penyimpanan agar fitur *Storage Bridge* (Load/Save bot) dapat mengakses folder internal.

---

### 🍏 2. iOS / iPadOS (iPhone & iPad)
Target OS: `MinimumOSVersion: 12.0` (kompatibel dari iOS 12, 13, 14, 15 hingga iOS 16, 17, 18+).

#### Opsi A: Instalasi Native (.ipa)
Gunakan salah satu metode sideloading berikut:
1. **AltStore / Sideloadly / SideStore**: Sambungkan perangkat ke PC/Mac, seret file `AlterDarkBot 4.1 (iOS).ipa`, lalu install menggunakan Apple ID gratis.
2. **TrollStore** *(iOS 14.0 - 16.6.1 & 17.0)*: Instal permanen tanpa batasan masa berlaku 7 hari dan tanpa perlu revoke.
3. **Scarlet / Esign / GBox**: Sideload langsung dari perangkat iOS kamu.

#### Opsi B: Metode Web / Safari PWA (Tanpa PC & Tanpa Sideload)
Memanfaatkan engine Ruffle WebAssembly langsung di peramban Safari:
1. Jalankan server lokal di PC dengan mengeklik ganda `Run_iOS_Server.bat` yang ada di dalam folder `ADB 4.1 Web iOS (Safari-PWA)`.
2. Buka **Safari** di iPhone/iPad kamu yang terhubung ke jaringan Wi-Fi yang sama, lalu akses alamat IP PC kamu (contoh: `http://192.168.1.xxx:8080/`).
3. **Mode Fullscreen (PWA)**:
   - Tap tombol **Share** (ikon kotak dengan panah ke atas).
   - Pilih **"Add to Home Screen"** (*Tambahkan ke Layar Utama*).
4. Kamu juga dapat menginstal profil `ADB 4.1 (iOS WebClip).mobileconfig` untuk pintasan instan berikon resmi di homescreen.

---

### 💻 3. Windows PC
File: `ADB Ver.3.0 (Anti-Freeze Flash).exe` atau `ADB Ver.3.0.exe`
1. Pastikan dependensi Visual C++ Redistributable telah terpasang di PC kamu.
2. Ekstrak dan jalankan file `.exe`. Bot sudah dilengkapi dengan runtime Flash Anti-Freeze untuk mencegah stuttering dan memory freeze selama farming berjam-jam.

---

### 🍎 4. macOS
File: `ADB Ver.3.0_macOS.zip` / `ADB Ver 3.0.app`
1. Ekstrak file `.zip` ke folder `Applications`.
2. Jika muncul peringatan keamanan *"App from unidentified developer"*, buka **System Settings > Privacy & Security**, lalu klik **Open Anyway**.

---

## 🛠️ Panduan Penggunaan Singkat (Quick Start)

1. **Login ke Akun AQW**: Masukkan username dan password pada menu game client, lalu pilih server yang diinginkan (disarankan server sepi jika farming bot intensif).
2. **Buka Menu Bot**: Tekan tombol menu bot di pojok layar untuk membuka antarmuka ADB.
3. **Memuat Bot Script**:
   - Masuk ke tab **Bot List**.
   - Arahkan ke direktori penyimpanan script kamu.
   - Pilih skrip bot yang ingin dijalankan, baca informasi author & target, lalu klik **Load**.
4. **Menjalankan Bot**:
   - Kembali ke tab utama bot.
   - Pastikan opsi drops dan safe rest sudah diatur.
   - Tekan tombol **Start** untuk memulai otomasi.
5. **Membuat Script Sendiri**:
   - Manfaatkan tombol *Grab Cell*, *Grab Coor*, *Kill Monster*, dan *Add Skill* untuk menyusun skrip otomasi baru sesuai kebutuhan farming kamu.

---

## 📁 Struktur Direktori Penting

```text
├── ADB/                              # Source ActionScript dan Asset GUI Flash (DarkMystic v3 engine)
│   ├── darkmystic/v3/bots/           # Modul logika bot, combat, options, quest, dan skill
│   └── ALTERDARKBOT_fla/             # Desain antarmuka UI komponen Flash
├── ADB 4.1 Web iOS (Safari-PWA)/     # Paket Web PWA & Ruffle WebAssembly untuk iOS Safari
│   ├── index.html                    # Web app container
│   ├── ruffle.js / *.wasm            # Engine Ruffle WebAssembly
│   └── Run_iOS_Server.bat            # Quick local server launcher
├── ADB 4.1 (iOS).ipa                 # Paket aplikasi native untuk iOS
├── ADB 4.1 (Ruffles).apk             # Paket aplikasi Android (16 KB page-aligned)
├── ADB Ver.3.0 (Anti-Freeze).exe     # Standalone client executable untuk Windows PC
├── ADB Ver 3.0.app                   # Standalone application bundle untuk macOS
├── all_tabs_dump.txt                 # Dokumentasi nama komponen UI dan tab kontrol
├── Readme Android.txt                # Catatan teknis Android APK
└── Readme iOS.txt                    # Catatan teknis iOS IPA & PWA
```

---

## ⚠️ Disclaimer & Catatan Keamanan

> [!WARNING]
> Aplikasi ini dibuat semata-mata untuk **tujuan edukasi, penelitian arsitektur sistem, dan eksplorasi teknologi cross-platform (ActionScript/WASM/Harman AIR)**.
> 
> Penggunaan aplikasi pihak ketiga (*botting*) melanggar **Terms of Service (ToS)** resmi dari *Artix Entertainment*. Gunakan dengan bijak dan atas risiko serta tanggung jawab pribadi masing-masing (*Use at your own risk*).

---

## 🤝 Kontribusi & Dukungan
Jika kamu menemukan bug atau memiliki ide perbaikan performa untuk engine Ruffle maupun Harman AIR, silakan buat issue atau pull request di repository ini. Happy farming! 🛡️⚡
