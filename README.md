# ⚔️ AlterDarkBot (ADB) / Spider Suite — AQW Cross-Platform Bot Client

[![Version](https://img.shields.io/badge/Version-v4.1%20Release-blue.svg?style=for-the-badge&logo=appveyor)](https://github.com)
[![Platform](https://img.shields.io/badge/Platform-Android%20%7C%20iOS%20%7C%20Windows%20%7C%20macOS%20%7C%20Web%20PWA-success.svg?style=for-the-badge&logo=android)](https://github.com)
[![Engine](https://img.shields.io/badge/Engine-ActionScript%203%20%2F%20Ruffle%20WASM%20%2F%20Harman%20AIR-orange.svg?style=for-the-badge&logo=adobe)](https://github.com)
[![Architecture](https://img.shields.io/badge/Android-16KB%20Page--Aligned%20(ARM32%2F64)-purple.svg?style=for-the-badge&logo=google)](https://github.com)
[![Syntax Status](https://img.shields.io/badge/AS3%20Syntax-100%25%20Balanced%20(167%2B%20Files)-brightgreen.svg?style=for-the-badge&logo=checkmarx)](https://github.com)

**AlterDarkBot (ADB) / Spider Suite** adalah client game dan otomasi canggih serbaguna untuk *AdventureQuest Worlds* (AQW). Dibangun dengan fondasi arsitektur ganda (**Spider Client Engine** & **DarkMystic v3 Core**) serta didukung engine modern **Ruffle WebAssembly** dan **Harman Adobe AIR**, ADB dirancang untuk memberikan pengalaman otomasi farming, questing, dan combat yang sangat ringan, mulus (*anti-stuttering*), dan bebas crash di seluruh ekosistem perangkat: **Android**, **iOS / iPadOS**, **Windows PC**, **macOS**, maupun **Web Browser (PWA)**.

---

## 📑 Daftar Isi
1. [🌟 Fitur Unggulan](#-fitur-unggulan)
2. [🏗️ Arsitektur Sistem & Modul Utama](#️-arsitektur-sistem--modul-utama)
3. [⚡ Optimasi Performa & Anti-Lag Engine](#-optimasi-performa--anti-lag-engine)
4. [📜 Format Script Bot (.adb)](#-format-script-bot-adb)
5. [📱 Panduan Lintas Platform (Cross-Platform)](#-panduan-lintas-platform-cross-platform)
6. [🛠️ Pipeline Otomasi, Validasi & Rilis](#️-pipeline-otomasi-validasi--rilis)
7. [📁 Peta Struktur Direktori Project](#-peta-struktur-direktori-project)
8. [❓ Pertanyaan Umum & Troubleshooting](#-pertanyaan-umum--troubleshooting)
9. [⚠️ Disclaimer & Legal](#️-disclaimer--legal)

---

## 🌟 Fitur Unggulan

### ⚔️ 1. Modern Bot Manager (`BotManager.as`)
- **Eksekusi Logika Fleksibel**: Mendukung conditional statements berbasis inventory, bank, temp inventory, posisi map, frame cell/pad, hingga status monster.
- **Lompatan Baris Instan ($O(1)$ Label Map)**: Sistem indeks kamus instan untuk perintah `gotolabel` dan penanda `label` tanpa overhead regex scanning.
- **Combat & Target Hunting**:
  - Serang monster spesifik berdasarkan nama atau gunakan mode wildcard/acak (`*` / `Kill Random`).
  - **Hunt for Items**: Otomatis memburu monster target sampai jumlah item terpenuhi (baik Regular maupun Temporary Inventory).
- **Advanced Skill Engine**:
  - Pengaturan urutan skill kustom dengan sinkronisasi Global Cooldown (GCD).
  - **Smart AI Skill**: Mode kecerdasan buatan adaptif yang membaca status HP, mana, dan kondisi aura/buff class secara realtime.
- **Drop Management Berkecepatan Tinggi**:
  - *Pickup All Drops* / *Pickup Whitelist Only* / *Pickup AC-Tagged Drops*.
  - *Decline All Drops* & *Reject Non-Whitelist*.
  - Menggunakan pre-normalized memory caching untuk verifikasi drop instan tanpa menyentuh display object tree.
- **Multi-Quest Automation**:
  - Load, Accept, dan Try Complete banyak Quest ID secara simultan.
  - Safe combat exit sebelum turn-in untuk mencegah penolakan dari server.
- **Embedded Offline Presets**: Tersedia puluhan skrip bot bawaan siap pakai (seperti *Void Aura*, *Legion Fealty*, *Nulgath Nation*, *Dragon of Time*, dll).
- **Mobile Storage Bridge**: Integrasi Android SAF (Storage Access Framework) & iOS filesystem untuk Load/Save skrip langsung dari folder internal perangkat.

### 📍 2. Dynamic Quest Tracker HUD (`QuestTrackerMenu.as`)
- **Dual Display Interface**:
  - **Mini Floating HUD**: Tampilan ringkas di layar permainan yang menampilkan quest aktif, progress item requirement, dan persentase penyelesaian.
  - **Full Detail Window**: Panel komprehensif untuk membaca seluruh daftar reward, target item, deskripsi, dan lokasi farm.
- **Intelligent Wiki / Database Search**:
  - Menghubungkan nama monster target ke direktori map dan cell secara otomatis.
  - Fallback aman langsung ke lokasi map dan cell/pad saat ini tanpa stuck di placeholder.
- **Aksi Cepat Interaktif**:
  - `[ 🔍 Scan ]`: Memindai ulang progress requirement quest dari inventory.
  - `[ ⚡ GO ]`: Berpindah instan ke Cell dan Pad monster target.
  - `[ 🚀 Join ]`: Langsung bergabung ke room/map tempat monster berada.
  - `[ 🌐 Wiki ]`: Membuka halaman resmi AQWWiki melalui browser eksternal tanpa menggantung thread Flash.
- **High-Readability Console Font**: Desain tipografi gaya console/code dengan kontras tinggi sehingga teks tetap tajam dan mudah dibaca bahkan pada mode grafis terendah (*Low Quality*).

### ⚙️ 3. Client Tweaks & Game Optimizer (`OptionMenu.as`)
- **Lag Killer Engine**:
  - Mematikan animasi monster, skill vector FX, animasi jubah/helm, dan ground rendering.
- **Crowd Optimizer**:
  - Otomatis menyembunyikan (*auto-hide*) pemain lain dan pet mereka di room yang ramai tanpa menghilangkan avatar karakter sendiri.
- **FPS Enforcer & Uncapper**:
  - Buka batas FPS game hingga **60 FPS** atau **120 FPS** untuk gameplay yang sangat halus.
- **Dynamic Camera Controller**:
  - Zoom In / Zoom Out bebas, horizontal & vertical pan, serta mode kamera bebas (*Free Camera*).
- **Chat & Filter Enhancements**:
  - Bypass filter sensor kata, notifikasi audio whisper, dan penanda waktu pesan (*timestamps*).

### 🧰 4. Paket Tool Bantu Tambahan (Auxiliary Modules)
- **Packet Menu (`PacketMenu.as`)**: Interseptor, logger, pengirim paket custom manual, dan automated packet spammer.
- **Fast Travels (`FormFastTravels.as`)**: Navigasi instan satu klik ke berbagai map farming vital, boss room, dan kota utama.
- **Instant Equipment (`FormInstantEquipment.as`)**: Penggantian set armor, senjata, helm, dan cape secara instan dalam 1 klik.
- **Maid Remake (`FormMaidRemake.as`)**: Pembersih otomatis inventory, transfer bank bulk, dan pengatur loadout.
- **Monster Drops Calculator (`FormMonsterDrops.as`)**: Inspeksi langsung tingkat persentase drop monster di cell aktif.
- **Room Radar (`FormRadar.as`)**: Radar visual posisi pemain lain, koordinat X/Y, dan status combat di dalam room.
- **Cell Grabber (`CellGrabber.as`)**: Inspektur cell dan pad untuk penyusunan rute skrip bot.
- **SWF Cosmetics Loader (`FormSWFCosmetics.as`)**: Muat aset kosmetik SWF kustom di sisi client untuk pratinjau tampilan gear.
- **Hardware Profiler (`PerformanceProfiler.as`)**: Monitor realtime penggunaan memori Flash Player, draw calls, dan frame rate.

---

## 🏗️ Arsitektur Sistem & Modul Utama

Repository ini mengintegrasikan komponen source ActionScript 3, FLA Adobe Animate, wrapper native, dan tooling build modern:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                       AlterDarkBot Cross-Platform Suite                     │
├────────────────────────────────┬────────────────────────────────────────────┤
│   🎮 Core Client (AS3 / FLA)   │          🌐 Runtime Cross-Platform         │
│  - Loader_Spider_fla           │  - Android: Harman AIR (16KB Page-Aligned) │
│    ├── BotManager.as           │  - iOS: Native IPA + Web PWA (Ruffle WASM) │
│    ├── QuestTrackerMenu.as     │  - Windows: Anti-Freeze Standalone EXE     │
│    ├── OptionMenu.as           │  - macOS: Native Wrapper Bundle            │
│    └── Auxiliary Tool Windows  │                                            │
├────────────────────────────────┴────────────────────────────────────────────┤
│                       📦 Tooling, Assets & Automation                       │
│  - Offline Knowledge Base: aqw_knowledge_base.json & lookup DB             │
│  - Verification: verify_as_syntax.js, verify_asset_integrity.js            │
│  - Release Engine: package_releases.js, publish_releases.js                │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Rincian Modul Inti:
1. **`Loader_Spider_fla/BotManager.as`**: Otak utama engine eksekusi botting, combat sequence, safe-rest loop, drop handling, dan integrasi storage bridge.
2. **`Loader_Spider_fla/QuestTrackerMenu.as`**: Engine tracker quest realtime terintegrasi HUD dan detail window.
3. **`Loader_Spider_fla/OptionMenu.as`**: Pusat konfigurasi client, visual tweaks, lag killer, crowd optimizer, dan FPS uncapper.
4. **`ADB/darkmystic/v3/bots/`**: Framework logika bot alternatif berbasis engine klasik DarkMystic v3.
5. **`ScriptLearn/`**: Arsitektur C# .NET desktop trainer / reference codebase (Grimoire/proxy style) untuk studi komunikasi packet dan flash interop.

---

## ⚡ Optimasi Performa & Anti-Lag Engine

Untuk mengatasi isu lag, stuttering (*patah-patah*), dan lonjakan beban CPU pada botting durasi panjang, serangkaian optimasi tingkat rendah telah diimplementasikan:

1. **Eliminasi Total Listener `Event.ENTER_FRAME` pada Stage**:
   - Menghilangkan listener frame 60 FPS pada `ensureSpoofLoop()` dan `updateAnonLoop()`.
   - Tugas spoofing dan anonimitas nama dipindahkan ke timer periodik hemat daya `featureTimer` (1000ms), membebaskan thread rendering Flash dari puluhan callback per detik.
2. **Indeks Lompatan $O(1)$ untuk `gotolabel`**:
   - Skrip bot besar (seperti *Void Aura* dengan 107 command dan puluhan loop) sebelumnya memindai array secara linier dengan regex berulang.
   - Kini menggunakan kamus hash `_labelIndexMap` yang diindeks saat bot mulai, sehingga waktu lompatan bersifat konstan dan bebas alokasi memori berlebih.
3. **Whitelist Drop Memory Cache (`_cachedNormWhitelist`)**:
   - Membandingkan nama drop langsung dengan pre-normalized string array di RAM tanpa melakukan traversal berulang ke komponen visual `list_WhitelistItems`.
4. **Dynamic Stage Quality Throttling**:
   - Saat bot aktif (`startBot()`), kualitas rasterisasi vector Flash otomatis diturunkan ke `StageQuality.LOW` untuk menghemat 40–70% beban CPU core. Kualitas tampilan otomatis dikembalikan saat bot berhenti (`stopBot()`).
5. **Caching Pencarian Nama Monster**:
   - Hasil sanitasi regex nama monster di-cache pada `onSkillTick` (350ms) sehingga tidak melakukan parsing ulang jika target monster tidak berganti.

---

## 📜 Format Script Bot (.adb)

Bot Manager menggunakan format JSON standar berlabel `.adb` (*AlterDarkBot Script*). Format ini terstruktur, mudah dibaca, dan kompatibel untuk diedit melalui teks editor maupun GUI Bot Manager:

```json
{
  "format": "AQW-BotManager",
  "version": 2,
  "cmdData": [
    { "type": "statement", "label": "Load Quest: 4432", "data": { "val": 4432, "condition": "Load Quest" } },
    { "type": "statement", "label": "Accept Quest: 4432", "data": { "val": 4432, "condition": "Accept Quest" } },
    { "type": "label", "label": "[Label] Check", "data": { "name": "Check" } },
    { "type": "statement", "label": "If Item not in Inventory: Astral Ephemerite Essence x20", "data": { "valName": "Astral Ephemerite Essence", "valQty": 20, "condition": "If Item not in Inventory" } },
    { "type": "gotolabel", "label": "Goto Label: AEE", "data": { "label": "AEE" } },
    { "type": "statement", "label": "Complete Quest: 4432", "data": { "val": 4432, "condition": "Complete Quest" } },
    { "type": "stopbot", "label": "Stop Bot: Selesai", "data": {} }
  ],
  "dropData": [
    { "type": "getdrop", "label": "Astral Ephemerite Essence", "data": { "name": "Astral Ephemerite Essence" } }
  ],
  "questData": [
    { "type": "quest", "label": "4432", "data": { "id": "4432" } }
  ],
  "skillData": [
    { "type": "skill", "label": "Skill 1", "data": { "slot": 1 } },
    { "type": "skill", "label": "Skill 2", "data": { "slot": 2 } }
  ],
  "settings": {
    "itemsTemp": false,
    "anonymous": false,
    "privateRoom": true
  }
}
```

### Tipe Perintah yang Didukung:
| Perintah | Deskripsi |
| :--- | :--- |
| `statement` | Evaluasi logika kondisi (Inventory, Bank, Temp, Map, Cell, Quest, dll). |
| `gotolabel` | Lompat ke nama label tertentu dalam waktu $O(1)$. |
| `label` | Penanda baris tujuan lompatan. |
| `kill` / `killrandom` | Menyerang monster spesifik atau sembarang target di cell aktif. |
| `killitem` | Memburu monster tertentu hingga jumlah item target tercapai. |
| `joinmap` | Bergabung ke room dan map tertentu (mendukung penomoran room privat). |
| `cell` | Berpindah ke nama Cell dan Pad tertentu. |
| `delay` | Memberikan jeda waktu eksekusi dalam satuan milidetik (ms). |
| `getitem` / `getdrop_id` | Mengambil item drop dari layar berdasarkan nama atau ID. |
| `useitem` | Menggunakan item konsumsi / consumable dari inventory. |
| `mapitem` | Mengambil map item interaktif berdasarkan Map Item ID. |
| `bank_transfer` | Memindahkan item secara otomatis dari/ke bank. |
| `stopbot` / `restart` | Menghentikan bot seketika atau mengulang dari baris pertama. |

---

## 📱 Panduan Lintas Platform (Cross-Platform)

| Platform | Format File Utama | Target OS | Engine / Arsitektur |
| :--- | :--- | :--- | :--- |
| **Android** | `AlterDarkBot_v4.1_Android_Ruffle.apk` | Android 10 s/d 16 | 16 KB Page-Aligned (ARM32/64), Ruffle / Harman AIR |
| **iOS / iPadOS** | `AlterDarkBot_v4.1_iOS.ipa` | iOS 12.0 s/d 18+ | Native IPA (Sideload / TrollStore) |
| **iOS (PWA)** | `AlterDarkBot_v4.1_PWA_Offline.zip` | iOS Safari | WebAssembly PWA (No Sideload / No PC) |
| **Windows** | `AlterDarkBot_v3.0_Windows_AntiFreeze.exe` | Windows 7, 8, 10, 11 | Anti-Freeze Flash Player Projector Standalone |
| **macOS** | `ADB Ver.3.0_macOS.zip` | macOS Catalina s/d Sequoia | Native Mac Wrapper Bundle |

### 🤖 1. Android Installation
- **16 KB Page Alignment**: Memenuhi persyaratan Google Play & Android 15/16 terbaru untuk stabilitas memori tingkat kernel.
- **Langkah Instalasi**:
  1. Unduh file `.apk` ke memori perangkat.
  2. Buka file installer dan izinkan pemasangan dari *Unknown Sources*.
  3. Berikan izin akses penyimpanan saat pertama kali membuka aplikasi agar fitur Load/Save bot dapat mengakses file lokal.

### 🍏 2. iOS / iPadOS Installation
- **Opsi A: Sideloading Native IPA** (`AlterDarkBot_v4.1_iOS.ipa`):
  - Pasang menggunakan **TrollStore** (permanen tanpa batas 7 hari pada iOS yang didukung), **AltStore**, **Sideloadly**, atau **SideStore**.
- **Opsi B: Safari Web PWA** (`ADB 4.1 Web iOS (Safari-PWA)`):
  - Tanpa perlu PC atau sertifikat developer Apple.
  - Buka folder PWA dan jalankan `Run_iOS_Server.bat` di PC yang berada pada jaringan Wi-Fi lokal yang sama.
  - Akses alamat IP PC di Safari iPhone/iPad kamu (misal: `http://192.168.1.50:8080`).
  - Ketuk tombol **Share > Add to Home Screen** untuk menjalankan dalam mode layar penuh (PWA) lengkap dengan audio unlock dan database lookup offline.

### 💻 3. Windows & macOS
- **Windows**: Ekstrak dan jalankan `AlterDarkBot_v3.0_Windows_AntiFreeze.exe`. Dilengkapi runtime Anti-Freeze untuk mencegah stuttering dan freeze grafis saat botting berhari-hari.
- **macOS**: Ekstrak `ADB Ver.3.0_macOS.zip` ke folder `/Applications`. Jika terhalang Gatekeeper, izinkan aplikasi melalui **System Settings > Privacy & Security > Open Anyway**.

---

## 🛠️ Pipeline Otomasi, Validasi & Rilis

Project ini dilengkapi seperangkat script otomasi pengujian dan build verifikasi berbasis Node.js:

```bash
# 1. Validasi Sintaks & Keseimbangan Delimiter AS3 (167+ File ActionScript):
node verify_as_syntax.js --all

# 2. Verifikasi Integritas Biner SWF, Magic Header (CWS/FWS), dan Dimensi Stage:
node verify_asset_integrity.js --verify

# 3. Sinkronisasi & Verifikasi Knowledge Base AQW Offline:
node build_knowledge_cache.js --verify

# 4. Bangun Paket Rilis Multiplatform ke Folder dist/ (Lengkap dengan SHA-256):
node package_releases.js

# 5. Verifikasi Kriptografis Artefak Rilis:
node package_releases.js --verify
```

---

## 📁 Peta Struktur Direktori Project

```text
C:\Users\MyBook Hype\Downloads\Source\
├── Loader_Spider_fla/                # Source ActionScript 3 Utama Spider Client Engine
│   ├── BotManager.as                 # Pusat kendali bot, combat, drops, quests, dan optimasi CPU
│   ├── QuestTrackerMenu.as           # Antarmuka Quest Tracker HUD, Detail Window, dan Wiki search
│   ├── OptionMenu.as                 # Menu pengaturan client, Lag Killer, Crowd Optimizer, FPS uncapper
│   ├── GrabQuestWindow.as            # Jendela pencari dan penarik quest aktif
│   ├── PacketMenu.as                 # Interseptor dan spammer paket jaringan server
│   ├── CellGrabber.as                # Pemeriksa Cell & Pad map
│   ├── FormFastTravels.as            # Navigasi cepat antar map/room
│   ├── FormGETITEM.as                # Pemeriksa dan pengambil drop item
│   ├── FormInstantEquipment.as       # Penukar perlengkapan otomatis
│   ├── FormMaidRemake.as             # Pembersih inventory dan penata bank
│   ├── FormMonsterDrops.as           # Kalkulator drop rate monster
│   ├── FormRadar.as                  # Radar posisi pemain di room
│   ├── PerformanceProfiler.as        # Pemantau frame rate dan pemakaian RAM
│   └── EmbeddedPresetBots.as         # Kumpulan skrip bot bawaan (Void Aura, Legion, Nulgath, dll)
├── ADB/                              # Source ActionScript & Asset GUI Flash DarkMystic v3
│   └── darkmystic/v3/bots/           # Modul logika bot legacy DarkMystic
├── ADB 4.1 Web iOS (Safari-PWA)/     # Paket Web PWA & Ruffle WebAssembly iOS
│   ├── index.html                    # Web App container (Viewport dinamis, audio unlock)
│   ├── aqw_lookup_db.json            # Database lookup ringkas item/monster/map
│   ├── ruffle.js / *.wasm            # Engine Ruffle WebAssembly
│   └── Run_iOS_Server.bat            # Server lokal satu klik untuk streaming ke Safari
├── dist/                             # Direktori Distribusi Rilis Produksi
│   ├── packages/                     # Paket installer siap pakai
│   │   ├── AlterDarkBot_v4.1_Android_Ruffle.apk
│   │   ├── AlterDarkBot_v4.1_iOS.ipa
│   │   └── AlterDarkBot_v3.0_Windows_AntiFreeze.exe
│   ├── AlterDarkBot_v4.1_PWA_Offline.zip
│   ├── AlterDarkBot_v4.1_PWA_Offline.7z
│   ├── RELEASE_MANIFEST.json         # Buku besar kriptografis SHA-256 & MD5
│   └── CHECKSUMS.txt                 # Daftar sha256sum standar GNU
├── ScriptLearn/                      # Reference Codebase C# .NET (Trainer / Grimoire Architecture)
├── aqw_knowledge_base.json           # Offline database lengkap (Drop, Monster, Map, dan Quests)
├── build_knowledge_cache.js          # Generator knowledge base dari database ActionScript
├── package_releases.js               # Engine pemaket rilis otomatis multiplatform
├── verify_as_syntax.js               # Validasi delimiter stack LIFO sintaks AS3
├── verify_asset_integrity.js         # Validasi integritas biner SWF dan checksum
├── publish_releases.js               # Tool distribusi dan rilis
└── README.md                         # Dokumentasi utama project
```

---

## ❓ Pertanyaan Umum & Troubleshooting

**Q: Mengapa game terasa berat / patah-patah saat Bot Manager dijalankan?**  
> **A:** Masalah ini telah diatasi secara tuntas pada pembaruan terkini. Pastikan Anda mengompilasi file terbaru dari [`BotManager.as`](file:///C:/Users/MyBook%20Hype/Downloads/Source/Loader_Spider_fla/BotManager.as). Listener `ENTER_FRAME` pada stage telah dihilangkan, sistem label telah menggunakan pencarian $O(1)$, dan kualitas stage otomatis disesuaikan ke `LOW` selama bot aktif demi kelancaran maksimal.

**Q: Bagaimana cara menambahkan Quest ID yang tidak ada di daftar?**  
> **A:** Buka menu **Quest Tracker** atau **Grab Quest Window**, masukkan ID Quest numerik pada kolom teks, lalu tekan **Load Quest** atau **Accept Quest**. Anda juga dapat menambahkannya ke dalam skrip bot melalui tab **Quest** pada Bot Manager.

**Q: Mengapa bot berhenti saat berpindah room?**  
> **A:** Pastikan opsi **Exit Combat On Join** aktif agar server game mengizinkan karakter keluar dari pertempuran sebelum berpindah map. Berikan jeda delay minimal 500–1000 ms setelah perintah `joinmap` agar aset SWF map selesai dimuat secara alami.

---

## ⚠️ Disclaimer & Legal

> [!WARNING]
> Perangkat lunak ini dibuat semata-mata untuk **tujuan edukasi, analisis sistem perangkat lunak, eksplorasi teknologi cross-platform (ActionScript 3, WebAssembly, dan Adobe AIR), serta penelitian efisiensi arsitektur game**.
> 
> Penggunaan otomasi pihak ketiga (*botting*) pada *AdventureQuest Worlds* bertentangan dengan **Terms of Service (ToS)** resmi dari *Artix Entertainment*. Segala konsekuensi, pemblokiran akun (*ban*), maupun risiko yang timbul akibat pemakaian aplikasi ini sepenuhnya merupakan **tanggung jawab pribadi pengguna masing-masing (*Use at your own risk*)**.

---

<p align="center">
  Dikelola dengan ❤️ oleh Komunitas Pengembang AlterDarkBot (GirayDev).
</p>
