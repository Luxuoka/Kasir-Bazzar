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
| ☁️ | **Login & Sinkronisasi Cloud** | Login menggunakan **Username & Password**. Data produk, transaksi, dan pengaturan otomatis tersinkron antar-perangkat (HP, tablet, laptop). |
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
| **Database & Auth** | Firebase Authentication (Username & Password) + Cloud Firestore (Realtime Multi-Device Sync) |
| **Penyimpanan Lokal** | Web Storage API (`localStorage`, key `kasir_bazaar_v2`) untuk mode offline & cache |
| **Ekspor Laporan** | [ExcelJS](https://github.com/exceljs/exceljs) v4.4.0 via jsDelivr CDN |

## 🚀 Cara Menjalankan

1. **Clone repository ini**

   ```bash
   git clone https://github.com/Luxuoka/NAMA_REPO.git
   cd NAMA_REPO
   ```

2. **Buka file `index.html` di browser**

   Tidak perlu build tool atau install dependency. Cukup klik dua kali `index.html` di laptop, tablet, atau smartphone Anda.

> 💡 Aplikasi butuh koneksi internet untuk memuat Vue, Firebase, ExcelJS, dan font dari CDN.

## ☁️ Menghubungkan ke Database Cloud (Firebase)

Agar kasir bisa login via **username & password** dan data tersimpan otomatis antar-perangkat (misal kasir pindah dari laptop ke HP):

1. Buka [Firebase Console](https://console.firebase.google.com/) (gratis dengan akun Google).
2. Klik **Add Project** dan beri nama proyek (misal `kasir-bazaar`).
3. Di menu sebelah kiri:
   - Pilih **Build → Authentication**, klik **Get Started**, lalu aktifkan provider **Email/Password**.
   - Pilih **Build → Firestore Database**, klik **Create Database**, dan pilih **Start in test mode**.
4. Klik ikon **⚙️ Project Settings** di kiri atas:
   - Pada bagian **Your apps**, klik ikon Web **`</>`**, daftarkan aplikasi, lalu salin objek `firebaseConfig`.
5. Buka `index.html` di browser:
   - Masuk ke tab **Laporan → Pengaturan → Atur Firebase**, lalu tempel kode konfigurasi dan klik **Simpan & Hubungkan**.
   - *(Opsional)* Anda juga bisa langsung menempelkannya ke objek `DEFAULT_FIREBASE_CONFIG` di dalam file `index.html` agar otomatis aktif di semua perangkat tanpa perlu input manual.

### 🔒 Rekomendasi Aturan Keamanan (Firestore Security Rules)
Agar setiap akun memiliki ruang penyimpanan toko masing-masing yang terisolasi aman:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## 📱 Penggunaan Multi-Device

- **Daftar Akun**: Masukkan username (misal: `kasir_stand1`) dan password (min. 6 karakter).
- **Pindah Perangkat**: Buka `index.html` di perangkat lain (HP kasir, tablet, laptop lain), lalu login dengan username dan password yang sama. Semua produk dan riwayat transaksi akan otomatis muncul seketika!
- **Realtime**: Transaksi baru di perangkat A akan langsung terupdate di perangkat B secara otomatis.
- **Cadangan Arsip**: Tetap disarankan mengunduh rekap Excel harian di tab Laporan sebagai arsip fisik bazaar.

---

<div align="center">

**Dibuat dengan 💜 oleh [Putra Cikal Asmarandana](https://github.com/Luxuoka)**

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:24243e,50:302b63,100:0f0c29&height=100&section=footer" width="100%" />

</div>
