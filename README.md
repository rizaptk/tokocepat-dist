# TokoCepat

**TokoCepat** adalah aplikasi Point of Sale (POS) atau sistem kasir berkinerja tinggi dengan pendekatan *offline-first*. Dirancang sebagai aplikasi native untuk platform **Desktop (Windows/OS Lain)** dan **Android Tablet** menggunakan **Tauri Framework** [1]. 

Ditenagai oleh **FireLite**, database dokumen *embedded* berbasis Rust-native, TokoCepat memprioritaskan kecepatan transaksi instan, integritas data keuangan, keamanan enkripsi *at-rest*, serta kemampuan sinkronisasi data lokal tanpa ketergantungan pada koneksi internet eksternal [1].

## ✨ Fitur Utama

-   **Arsitektur Native & Offline-First**: Aplikasi berjalan secara native di Desktop dan Android Tablet melalui Tauri (v2), menyimpan data secara lokal pada database dokumen berkinerja tinggi **FireLite** (terinspirasi dari Google Firestore dengan arsitektur embedded sekelas SQLite) [1].
-   **Sinkronisasi Jaringan Lokal (Net Sync)**: Mengimplementasikan sistem replikasi mesh peer-to-peer hibrida berbasis mDNS untuk sinkronisasi database lokal antar perangkat dalam jaringan LAN yang sama tanpa membutuhkan koneksi internet [1].
-   **Kemitraan Konsinyasi (Titipan)**: Manajemen barang titipan harian/periodik yang komprehensif, mendukung komisi fleksibel (persentase/flat), pengosongan stok retur otomatis, pelacakan status pembayaran (*unpaid/paid*), serta buku besar payout yang terintegrasi langsung dengan laci kasir [1].
-   **UI Cepat & Responsif**: Antarmuka kasir yang dioptimalkan untuk operasional kilat menggunakan React (v19) dan Tailwind CSS (v4) [1].
-   **Manajemen Produk & Bahan Baku**: Mendukung tipe produk ritel dan F&B, termasuk varian, modifier kompleks, dan pelacakan bahan baku berbasis resep harian.
-   **Kontrol Inventori Terintegrasi**: Pemotongan stok otomatis saat penjualan serta modul penyesuaian stok manual dengan log audit yang mencatat alasan mutasi secara terperinci [5].
-   **Integritas Keuangan**: Mengimplementasikan sistem sif yang ketat (Buka/Tutup Sif) untuk rekonsiliasi kas dan buku besar transaksi yang tidak dapat diubah (immutable).
-   **Integrasi Perangkat Keras Native**: Mendukung pemindai barcode (kamera tablet maupun hardware USB eksternal), laci kasir otomatis via Kick Pin printer, dan pencetakan struk thermal melalui protokol ESC/POS [1].
-   **Laporan Mendalam**: Menyediakan laporan mendetail untuk penjualan, inventaris, pergerakan stok, dan konsumsi bahan baku, dengan opsi ekspor ke Excel dan PDF menggunakan API Tauri native save dialog [1].

## 🚀 Rilis Terbaru (v0.3.2) - Pengoptimalan Pelunasan & Buku Besar Konsinyasi

Pembaruan versi **v0.3.2** mematangkan integrasi performa database **FireLite** dan mengoptimalkan fleksibilitas operasional harian bagi hasil kemitraan konsinyasi [1].

Beberapa perubahan, perbaikan, dan peningkatan meliputi:

### 🌟 Fitur & Pengoptimalan Baru
-   **Pelacakan Pembayaran Presisi (*Paid vs Unpaid*)**: Sistem kini melacak status bagi hasil (*settlement*) per baris transaksi konsinyasi harian. Ini mencegah terjadinya klaim pembayaran ganda (*double payout*) oleh vendor saat memilih rentang tanggal yang luas [5].
-   **Buku Besar Riwayat Pembayaran (Payout Ledger)**: Laporan Konsinyasi kini memiliki dua wajah. Jika status filter diubah ke *"Sudah Lunas"*, laporan otomatis beralih fungsi menjadi buku jurnal pembayaran kronologis berdasarkan tanggal penyerahan dana secara mendetail [5].
-   **Transaksi Atomik Berkinerja Tinggi (Write Batch)**: Proses pengosongan stok sisa, pembuatan log mutasi retur, pelunasan baris transaksi, hingga penyesuaian kas laci kasir digabungkan dalam satu transaksi atomik **`writeBatch` FireLite** [5]. Mengeliminasi bottleneck komunikasi IPC Tauri dan menjamin konsistensi data [1].
-   **Siklus Payout & Retur Fleksibel**: Menghapus keterikatan waktu harian. Pemasok kini dapat menarik retur sisa barang, memasok barang baru (*restock*), atau mencairkan dana bagi hasil kapan saja mereka inginkan (harian, mingguan, bulanan, atau kondisional) [5].
-   **Peringatan Sif Kasir Terintegrasi**: Menyediakan kotak peringatan taktil (*Stylish Warning Alert*) berbasis ikon `AlertTriangle` di halaman laporan yang membatasi tindakan pelunasan jika kasir belum membuka sif aktif guna mencegah selisih pembukuan [1].

### 🛠️ Perbaikan Bug (Bug Fixes)
-   **Perbaikan Gambar Placeholder Broken**: Memperbaiki penayangan gambar demo untuk produk Kue Lapis (ID: `13`) dan Donat Kentang (ID: `14`) menggunakan visual Unsplash berkualitas tinggi dan sinkron dengan sistem seeder [5].
-   **Perbaikan Stok Negatif Seeding**: Mengatasi masalah stok produk konsinyasi yang minus saat seeding awal dengan menyertakan mereka ke dalam siklus pasok berkala dan pengosongan harian secara otomatis [5].
-   **Pelunyapan Teks "Tanpa Keterangan"**: Menambahkan detail data `reason` pada seluruh mutasi stok simulasi sehingga kartu riwayat inventori tampil informatif [5].

---

## 🔄 Riwayat Rilis Sebelumnya

### v0.3.1 - Manajemen Konsinyasi / Titipan Dasar
-   **Skema Komisi Fleksibel**: Mendukung bagi hasil berdasarkan **Persentase (%)** dari nilai jual atau **Flat / Nominal Tetap (Rp)** per unit item terjual.
-   **Manajemen Form Produk Pintar**: Menghilangkan kolom Harga Modal (*cost price*) secara dinamis pada produk konsinyasi untuk mencegah tumpang tindih data, serta membersihkan nilai modal secara otomatis saat formulir disimpan.
-   **Pemisahan HPP & Liabilitas Titipan**: Menyempurnakan Laporan Penjualan dan Audit Laba & Kas dengan memisahkan nilai aset HPP toko dari kewajiban biaya bagi hasil konsinyasi. Hal ini menjaga keakuratan analisis margin keuntungan riil toko Anda tanpa distorsi angka modal.
-   **Antarmuka Kasir Informatif**: Menambahkan penanda (*badge*) visual bertuliskan "Titipan" serta nama penitip pada baris keranjang kasir (*Classic & Default Cashier*) dan modal riwayat transaksi sif untuk memudahkan identifikasi oleh operator kasir.
-   **Ekspor Dokumen yang Diperbarui**: Fungsi ekspor laporan penjualan dan audit ke Excel (.xlsx) & PDF (.pdf) kini mendukung visualisasi kolom HPP Standar, Bagi Hasil Titipan, Pajak, dan Laba Bersih secara terpisah.
