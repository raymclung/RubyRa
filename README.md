<div align="center">

<img src="assets/img-01.svg" alt="RubyRa" width="88">

# RubyRa Stays

**Prototipe antarmuka pemesanan penginapan — hotel, villa, resort, guest house, dan homestay.**

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)](https://developer.mozilla.org/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/docs/Web/JavaScript)
[![Single Page](https://img.shields.io/badge/SPA-satu%20berkas-800002?style=flat-square)](#-teknologi)
[![No Framework](https://img.shields.io/badge/Framework-none-C8A24B?style=flat-square)](#-teknologi)
[![License: MIT](https://img.shields.io/badge/License-MIT-800002?style=flat-square)](LICENSE)

[**Lihat Demo →**](https://raymclung.github.io/RubyRa/)

</div>

---

> [!IMPORTANT]
> **Ini prototipe antarmuka (UI prototype), bukan aplikasi produksi.**
> Belum ada server maupun basis data. Data penginapan ditulis langsung di dalam kode, dan
> pemesanan tidak benar-benar tercatat di mana pun. Halaman masuk hanya simulasi tampilan —
> tidak ada autentikasi sungguhan.

## 📖 Tentang

**RubyRa Stays** adalah rancangan aplikasi pemesanan penginapan bergaya marketplace. Seluruh
perjalanan pengguna tergambar utuh: menelusuri kategori, menyaring hasil pencarian, membuka
detail properti beserta galeri dan ulasan, memilih tanggal lewat kalender, mengisi data
pemesanan, membayar, sampai melihat riwayat pesanan.

Menariknya, **seluruh aplikasi ini berada dalam satu berkas `index.html`** — 13 layar, 53 fungsi
JavaScript, dan sistem desain lengkap, semuanya dalam 100 KB. Tanpa framework, tanpa langkah
build, tanpa satu pun dependensi.

Palet warnanya mengambil nama proyek: **ruby** `#800002` dipadu **gold** `#C8A24B`.

## ✨ Fitur

| | Fitur | Keterangan |
|---|---|---|
| 🔍 | **Pencarian & filter** | Saring berdasarkan harga, kategori, dan penawaran khusus, lengkap dengan pengurutan |
| 🏨 | **Detail properti** | Galeri gambar yang bisa ditukar, daftar kamar, fasilitas, dan ulasan tamu |
| 📅 | **Kalender pemesanan** | Pemilih tanggal buatan sendiri, menghitung jumlah malam secara otomatis |
| 💳 | **Alur pembayaran** | Beberapa metode bayar dengan indikator progres bertahap |
| ❤️ | **Wishlist** | Simpan properti favorit, ikon hati tersinkron di seluruh layar |
| 📋 | **Riwayat pesanan** | Daftar pemesanan beserta rinciannya |
| 👤 | **Akun** | Simulasi masuk dan pendaftaran, dengan validasi formulir |
| 💬 | **Pusat bantuan** | Daftar pertanyaan umum dengan panel yang bisa dibuka-tutup |
| 🎨 | **Halaman Design System** | Etalase warna, tipografi, dan komponen — terpasang di dalam aplikasi |

## 🖥️ Daftar layar

Ketiga belas layar dikelola oleh satu fungsi navigasi `go()`, yang menyembunyikan dan menampilkan
bagian sesuai `id`-nya:

| | | |
|---|---|---|
| `screen-home` — beranda | `screen-results` — hasil pencarian | `screen-detail` — detail properti |
| `screen-booking` — formulir pesan | `screen-payment` — pembayaran | `screen-confirm` — konfirmasi |
| `screen-bookings` — pesanan saya | `screen-wishlist` — favorit | `screen-profile` — profil |
| `screen-login` — masuk | `screen-signup` — daftar | `screen-help` — bantuan |
| `screen-style` — design system | | |

## ⚡ Catatan optimasi

Versi awal berkas ini berukuran **31,6 MB** karena seluruh gambar ditanam sebagai
[data URI base64](https://developer.mozilla.org/docs/Web/URI/Schemes/data) langsung di dalam HTML —
satu barisnya saja mencapai 25 MB. Akibatnya berkas tidak bisa diunggah lewat antarmuka web GitHub
(batasnya 25 MB), berat dibuka browser, dan mustahil di-*review*.

Gambar-gambar tersebut dikeluarkan menjadi berkas tersendiri, lalu dikompres:

| | Sebelum | Sesudah | |
|---|---:|---:|---|
| `index.html` | 31,6 MB | **97 KB** | 325× lebih kecil |
| Gambar | 19,0 MB | **2,5 MB** | hemat 87% |
| **Total** | **31,6 MB** | **2,7 MB** | |

Dari 37 gambar tertanam, hanya **19 yang benar-benar unik** — sisanya duplikat yang mengulang data
yang sama berkali-kali. Setelah dipisah, gambar juga bisa disimpan di cache browser, sehingga
kunjungan berikutnya jauh lebih ringan.

## 🚀 Menjalankan secara lokal

Tidak ada `npm install`, tidak ada proses build.

```bash
git clone https://github.com/raymclung/RubyRa.git
cd RubyRa
```

Buka `index.html` langsung di browser — selesai. Atau lewat server statis:

```bash
python -m http.server 8000
```

## 🛠️ Teknologi

| Aspek | Pilihan |
|---|---|
| **Bahasa** | HTML5, CSS3, JavaScript (ES6+) |
| **Arsitektur** | Aplikasi satu halaman dalam satu berkas — 41% markup, 31% JavaScript, 28% CSS |
| **Navigasi** | Perpindahan layar berbasis `id`, tanpa router |
| **Penataan gaya** | CSS murni dengan *custom properties* sebagai token desain |
| **Tipografi** | Inter dan Poppins (Google Fonts) |
| **Dependensi** | Tidak ada |

```css
:root{
  --ruby:#800002;  --ruby-dark:#5C0001;  --ruby-light:#A3232A;
  --gold:#C8A24B;  --gold-light:#E4CB82;
  --bg:#F5F5F5;    --card:#FFFFFF;       --ink:#1F2937;
}
```

## 📁 Struktur

```
RubyRa/
├── index.html          # seluruh aplikasi — 13 layar, 53 fungsi
├── assets/             # 19 gambar hasil ekstraksi dari base64
└── arsip/              # jejak proses desain
    ├── figma.html          # terjemahan awal dari rancangan Figma
    ├── mockup.html         # mockup statis
    ├── prototype.html      # prototipe interaktif
    ├── prototype-mobile.html
    └── desktop.html
```

### Tentang folder `arsip/`

Berisi tahapan desain sebelum aplikasi akhir terbentuk, dari terjemahan rancangan Figma sampai
prototipe yang bisa diklik. Kelimanya berdiri sendiri — buka langsung di browser untuk melihat
bagaimana rancangannya berkembang.

## 🗺️ Rencana pengembangan

Batasan yang disadari, dan langkah lanjutan bila proyek ini diteruskan:

- [ ] **Pisahkan berkas** — CSS dan JavaScript dikeluarkan dari `index.html` ke berkas tersendiri
- [ ] **Backend sungguhan** — REST API dan basis data untuk data properti serta pemesanan
- [ ] **Autentikasi** — saat ini masuk dan daftar hanya simulasi tampilan
- [ ] **Penyimpanan data** — wishlist dan pesanan masih hilang begitu halaman dimuat ulang
- [ ] **Pembayaran nyata** — integrasi payment gateway
- [ ] **Perbaiki `arsip/figma-to-html`** — hasil ekspor otomatis Figma; 39 rujukan gambarnya rusak, sehingga tidak disertakan

## 📄 Lisensi

Dirilis di bawah [Lisensi MIT](LICENSE).

---

<div align="center">
<sub>Dibuat oleh <a href="https://github.com/raymclung">@raymclung</a></sub>
</div>
