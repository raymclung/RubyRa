# RubyRa Stays

Prototipe antarmuka pemesanan penginapan — hotel, villa, resort, guest house, homestay.

[Lihat demo](https://raymclung.github.io/RubyRa/)

Dibuat sebagai tugas kuliah. Ini prototipe antarmuka, bukan aplikasi yang benar-benar berjalan. Tidak ada server,
tidak ada basis data. Data penginapannya ditulis langsung di dalam kode, dan pemesanan
tidak tercatat di mana pun. Halaman masuknya pun hanya simulasi tampilan.

## Bentuknya

Tiga belas layar — beranda, hasil pencarian, detail properti, alur pemesanan,
pembayaran, konfirmasi, riwayat pesanan, wishlist, profil, masuk, daftar, bantuan, dan
satu halaman design system — semuanya dalam **satu berkas `index.html`**. Ada 53 fungsi
JavaScript di dalamnya, 100 KB, tanpa framework dan tanpa satu pun dependensi.

Perpindahan antar layar diurus satu fungsi `go()` yang menyembunyikan dan menampilkan
bagian berdasarkan `id`. Tidak ada router.

Warnanya mengambil nama proyek: ruby `#800002` dipadu gold `#C8A24B`.

## Soal ukuran berkasnya

Versi pertama `index.html` berukuran **31,6 MB**. Penyebabnya semua gambar saya tanam
sebagai data URI base64 langsung di dalam HTML — satu barisnya saja mencapai 25 MB.

Akibatnya berkas ini tidak bisa diunggah lewat antarmuka web GitHub, yang membatasi
25 MB per berkas. Browser juga berat membukanya, dan berkasnya mustahil di-review.

Setelah gambarnya dikeluarkan menjadi berkas terpisah lalu dikompres:

|                | Sebelum  | Sesudah |
| -------------- | -------: | ------: |
| `index.html`   | 31,6 MB  | 97 KB   |
| Gambar         | 19,0 MB  | 2,5 MB  |
| **Total**      | 31,6 MB  | 2,7 MB  |

Yang mengejutkan: dari 37 gambar yang tertanam, ternyata hanya **19 yang benar-benar
unik**. Sisanya duplikat yang mengulang data sama berkali-kali. Setelah dipisah, gambar
juga bisa disimpan di cache browser sehingga kunjungan berikutnya jauh lebih ringan.

## Menjalankan

Tidak ada `npm install`, tidak ada proses build.

```bash
git clone https://github.com/raymclung/RubyRa.git
cd RubyRa
```

Buka `index.html` langsung di browser. Atau lewat server statis kalau mau:

```bash
python -m http.server 8000
```

## Isi folder

```
index.html      seluruh aplikasi
assets/         19 gambar hasil ekstraksi
arsip/          lima halaman proses desain
```

Folder `arsip/` berisi tahapan sebelum aplikasi akhir terbentuk — terjemahan awal dari
rancangan Figma, mockup statis, lalu prototipe yang bisa diklik untuk desktop dan mobile.
Kelimanya berdiri sendiri, tinggal dibuka di browser.

## Yang belum dikerjakan

- CSS dan JavaScript masih menyatu di dalam `index.html`, belum dipisah
- Belum ada backend, jadi wishlist dan pesanan hilang begitu halaman dimuat ulang
- Masuk dan daftar masih simulasi tampilan
- Data propertinya masih ditulis di dalam kode

## Lisensi

[MIT](LICENSE)
