# 🎯 EduMeetJob — Platform Karier Digital Indonesia

> **DIGDAYA × Hackathon 2026** — Platform AI-powered yang menghubungkan talenta digital Indonesia dengan peluang karier terbaik di seluruh nusantara.

![Platform Preview](https://img.shields.io/badge/Status-Hackathon%202025-blueviolet?style=for-the-badge)
![Tech](https://img.shields.io/badge/Tech-HTML%20%7C%20CSS%20%7C%20Vanilla%20JS-00d4ff?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-2dcc7a?style=for-the-badge)

---

## 📋 Daftar Isi

- [Overview](#overview)
- [Fitur Utama](#fitur-utama)
- [Tech Stack](#tech-stack)
- [Cara Menjalankan](#cara-menjalankan)
- [Struktur Halaman](#struktur-halaman)
- [Komponen UI](#komponen-ui)
- [Data & Logika](#data--logika)
- [Kontribusi](#kontribusi)

---

## 🔍 Overview

**EduMeetJob** adalah platform karier digital berbasis AI yang dirancang untuk membantu talenta Indonesia menemukan pekerjaan yang paling sesuai dengan profil dan skill mereka. Platform ini menggabungkan job matching cerdas, analisis skill gap, jalur pelatihan personal, dan peta peluang kerja antarwilayah dalam satu antarmuka yang terintegrasi.

Platform ini dibangun sebagai single-page application (SPA) murni menggunakan HTML, CSS, dan JavaScript vanilla — tanpa framework eksternal, siap dijalankan langsung di browser.

---

## ✨ Fitur Utama

### 🏠 Dashboard
Pusat kendali personal yang menampilkan ringkasan aktivitas, match score AI, KPI karier (jumlah lowongan cocok, lamaran aktif, kursus berjalan, sertifikat), serta panel aksi cepat.

### 🤖 AI Job Matching
Mesin pencarian lowongan berbasis AI yang menganalisis ribuan lowongan dan menampilkan hasil yang paling relevan. Dilengkapi filter multi-dimensi (kata kunci, lokasi, tipe kerja, min. match score, skill chips) dan insight personal dari AI untuk tiap lowongan.

### 📉 Skill Gap Advisor
Visualisasi radar interaktif yang membandingkan skill pengguna dengan requirement industri untuk 4 target role (Frontend Engineer, Full-Stack Developer, UI/UX Designer, Data Analyst), lengkap dengan rekomendasi kursus spesifik per skill gap.

### 📚 Personalized Training Path
Jalur belajar terstruktur dengan progress tracking, status kursus (selesai / aktif / terkunci), dan panel sertifikat. AI memilihkan urutan kursus berdasarkan skill gap pengguna.

### 📊 Analitik Karier
Dashboard data pasar kerja real-time: tren permintaan skill (bar chart), distribusi gaji (donut chart), trend match score (line chart), dan tabel industri dengan pertumbuhan & kompetisi.

### 🗺️ Job Matching Antarwilayah
Peta interaktif Indonesia yang menampilkan distribusi lowongan per kota, ranking kota berdasarkan jumlah lowongan cocok, serta filter tipe kerja (Remote, Hybrid, WFH Full, Relokasi Difasilitasi).

---

## 🛠️ Tech Stack

| Teknologi | Penggunaan |
|-----------|-----------|
| HTML5 | Struktur & semantik |
| CSS3 (Vanilla) | Desain sistem, animasi, layout |
| JavaScript (ES6+) | Logika aplikasi, manipulasi DOM |
| Google Fonts | Tipografi — Syne & DM Sans |
| SVG | Radar chart, peta wilayah, visualisasi data |

Tidak ada dependency eksternal — tidak perlu `npm install`, tidak perlu build tool.

---

## 🚀 Cara Menjalankan

### Metode 1 — Buka Langsung
```bash
# Cukup buka file di browser
open index.html
```

### Metode 2 — Live Server (Direkomendasikan)
```bash
# Dengan VS Code Live Server extension
# Klik kanan index.html → "Open with Live Server"

# Atau dengan Python
python -m http.server 8080

# Atau dengan Node.js
npx serve .
```

Kemudian buka `http://localhost:8080` di browser.

---

## 📁 Struktur Halaman

```
EduMeetJob (SPA)
│
├── #sidebar                  ← Navigasi tetap kiri
│   ├── Logo & branding
│   ├── Menu navigasi (6 halaman utama)
│   └── Profil pengguna + XP bar
│
├── #main
│   ├── .topbar               ← Header sticky
│   │
│   ├── #p-dashboard          ← Halaman Dashboard
│   ├── #p-matching           ← AI Job Matching
│   ├── #p-skillgap           ← Skill Gap Advisor
│   ├── #p-training           ← Personalized Training
│   ├── #p-analitik           ← Analitik Karier
│   └── #p-wilayah            ← Job Antarwilayah
│
├── #jobModal                 ← Modal detail lowongan
└── #toast                    ← Notifikasi global
```

---

## 🎨 Komponen UI

Platform menggunakan design system yang konsisten dengan CSS variables:

```css
--cyan:    #00d4ff   /* Aksen utama */
--violet:  #7b5fff   /* Aksen sekunder */
--pink:    #ff5fa0   /* Highlight / warning */
--green:   #2dcc7a   /* Sukses / positif */
--gold:    #ffd060   /* Peringatan / sedang */
--bg:      #04081a   /* Background utama (dark navy) */
```

Komponen yang tersedia: `.card`, `.tag`, `.btn-primary`, `.btn-outline`, `.progress-bar`, `.input`, `.select`, `.kpi`, `.job-card`, `.path-item`, `.city-item`, dan banyak lagi.

---

## 💡 Data & Logika

Semua data bersifat statis (hardcoded) dan dapat diganti dengan API call:

| Data | Variabel | Keterangan |
|------|----------|------------|
| Daftar lowongan | `jobs[]` | 6 lowongan sample dengan match score |
| Skill per role | `roleSkills{}` | 4 role x 6 skill, nilai mine vs req |
| Rekomendasi kursus | `roleRecos{}` | 4 role x 6 rekomendasi kursus |
| Data kursus | `courses[]` | 7 kursus dengan status & progress |
| Data kota | `cities[]` | 8 kota + koordinat peta SVG |
| Data industri | `anRows[]` | 7 industri dengan tren & gaji |

### Fungsi Utama

```js
nav(id, el)          // Navigasi antar halaman
filterJobs()         // Filter & render job cards
setRole(role, el)    // Ganti target role di Skill Gap
buildRadar()         // Render radar chart SVG
buildPathTrack()     // Render learning path
buildMap()           // Render peta wilayah SVG
toast(msg, ico)      // Tampilkan notifikasi global
```

---

## 🤝 Kontribusi

1. Fork repository ini
2. Buat branch baru: `git checkout -b feature/nama-fitur`
3. Commit perubahan: `git commit -m "feat: tambah fitur X"`
4. Push: `git push origin feature/nama-fitur`
5. Buat Pull Request

### Ide Pengembangan
- Integrasi API job board nyata (Kalibrr, Glints, LinkedIn)
- Backend autentikasi (Firebase / Supabase)
- AI matching dengan model NLP lokal
- Responsive mobile dengan sidebar drawer
- Dark/light mode toggle

---

## 📄 Lisensi

Proyek ini dilisensikan di bawah [MIT License](LICENSE).

---

<div align="center">

Dibuat dengan ❤️ untuk **DIGDAYA × Hackathon 2026**

*Membangun ekosistem karier digital Indonesia yang lebih inklusif*

</div>
