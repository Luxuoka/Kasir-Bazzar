<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f0c29,50:302b63,100:24243e&height=140&section=header" width="100%" />

# 🧾 Kasir Bazaar

### *Sistem Kasir Web untuk Bazaar, Tanpa Server, Tanpa Install*

Aplikasi kasir satu file yang berjalan sepenuhnya di browser. Catat penjualan, kelola produk, dan unduh laporan harian dalam format Excel.

<br/>

<img src="https://img.shields.io/badge/Vue.js_3-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white" alt="Vue.js 3" />
<img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript" />
<img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5" />
<img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3" />
<img src="https://img.shields.io/badge/ExcelJS-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white" alt="ExcelJS" />
<img src="https://img.shields.io/badge/Zero%20Build-14b8a6?style=for-the-badge&labelColor=1e1b4b" alt="Zero Build" />

</div>

---

## 📖 Tentang Proyek

**Kasir Bazaar** adalah sistem kasir berbasis web untuk keperluan bazaar. Dibangun dengan arsitektur **Single-File Web Application** tanpa build step, semuanya berjalan di sisi client sehingga **cukup klik ganda file HTML** untuk mulai dipakai, tanpa server Node.js atau PHP.

## ✨ Fitur Utama

| | Fitur | Deskripsi |
|---|---|---|
| 🛒 | **Kasir** | Pilih produk, filter kategori (Makanan / Minuman), lihat keranjang dan total secara langsung. |
| 💳 | **Multi Metode Bayar** | Mendukung **Cash**, **QRIS** (menampilkan gambar QRIS ke pembeli), dan **Kupon**. |
| 📦 | **Manajemen Produk** | Tambah, ubah nama/harga, dan hapus produk. Harga lama pada transaksi yang sudah tercatat tidak ikut berubah. |
| 📊 | **Laporan Harian** | Ringkasan total, Cash, QRIS, dan Kupon per tanggal beserta jumlah transaksi. |
| 📥 | **Ekspor Excel (.xlsx)** | Unduh laporan akuntansi bazaar langsung dari browser. |
| 🌗 | **Dark & Light Mode** | Mengikuti tema perangkat secara otomatis. |
| 📱 | **Mobile-friendly** | Tombol ramah sentuh dan tata letak responsif untuk tablet, smartphone, maupun laptop. |

## 📥 Isi Laporan Excel

File Excel yang dihasilkan memakai format laporan akuntansi bazaar dengan sheet berikut:

| Sheet | Isi |
|---|---|
| **Dana** | Rekap dana yang masuk |
| **Barang** | Daftar barang |
| **Penggunaan Dana** | Rincian penggunaan dana |
| **Laba Rugi** | Perhitungan laba rugi |
| **Penjualan** | Detail transaksi penjualan |

Dilengkapi border, merge cell, format mata uang Rupiah (`[$Rp-421]#,##0`), catatan, dan formula `SUM`.

## 🛠️ Teknologi yang Digunakan

<p>
  <img src="https://skillicons.dev/icons?i=vue,js,html,css&theme=dark" alt="Tech stack" />
</p>

| Komponen | Teknologi |
|---|---|
| **Arsitektur** | Serverless / Client-Side SPA (Single HTML File) |
| **Framework UI** | Vue.js 3 via CDN (Composition API: `ref`, `reactive`, `computed`, `watch`, `onMounted`, `<teleport>`) |
| **Styling** | Vanilla CSS3 (Custom Properties, Grid, Flexbox) + font Inter dari Google Fonts |
| **Penyimpanan** | Web Storage API (`localStorage`, key `kasir_bazaar_v2`) |
| **Ekspor Laporan** | [ExcelJS](https://github.com/exceljs/exceljs) v4.4.0 via jsDelivr CDN |

## 🚀 Cara Menjalankan

1. **Clone repository ini**

   ```bash
   git clone https://github.com/Luxuoka/NAMA_REPO.git
   cd NAMA_REPO
   ```

2. **Buka file `Sistem Kasir.html` di browser**

   Tidak perlu build tool atau install dependency. Untuk development yang lebih nyaman, gunakan ekstensi **Live Server** di VS Code.

> 💡 Aplikasi butuh koneksi internet untuk memuat Vue, ExcelJS, dan font dari CDN.

## ⚠️ Catatan Penggunaan

- Data (produk, transaksi, pengaturan, gambar QRIS) tersimpan di **localStorage browser perangkat** yang dipakai.
- Pakai **satu perangkat sebagai kasir** dan **unduh Excel setiap hari** sebagai cadangan.
- Menghapus data browser (clear site data) akan ikut menghapus semua data kasir.

---

<div align="center">

**Dibuat dengan 💜 oleh [Putra Cikal Asmarandana](https://github.com/Luxuoka)**

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:24243e,50:302b63,100:0f0c29&height=100&section=footer" width="100%" />

</div>
