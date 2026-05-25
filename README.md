# TokoCepat

**TokoCepat** adalah aplikasi Point of Sale (POS) atau sistem kasir berkinerja tinggi dengan pendekatan *offline-first*. Dirancang untuk berbagai jenis usaha, mulai dari toko ritel hingga kafe dan restoran. Dibangun dengan *tech stack* modern, TokoCepat memprioritaskan kecepatan transaksi, integritas data keuangan, dan kemampuan untuk beroperasi secara mulus tanpa ketergantungan pada koneksi internet yang stabil.

## ✨ Fitur Utama

-   **Operasional Offline-First**: Fungsi inti POS (penjualan, keranjang, kontrol sif) dirancang untuk bekerja sepenuhnya secara offline menggunakan database SQLite berbasis browser.
-   **UI Cepat & Responsif**: Antarmuka yang dioptimalkan untuk kasir, dibangun dengan Next.js, React, dan Tailwind CSS untuk pemrosesan penjualan yang kilat.
-   **Manajemen Produk Lengkap**: Mendukung tipe produk ritel dan F&B, termasuk varian, modifier kompleks, dan pelacakan bahan baku berbasis resep.
-   **Kontrol Inventori yang Kuat**: Fitur pemotongan stok otomatis saat penjualan serta modul penyesuaian stok manual dengan log audit untuk setiap pergerakan barang.
-   **Integritas Keuangan**: Mengimplementasikan sistem sif yang ketat (Buka/Tutup Sif) untuk rekonsiliasi kas dan buku besar transaksi yang tidak dapat diubah (immutable).
-   **Sistem Lisensi Aman**: Mesin lisensi hybrid online/offline yang memvalidasi lisensi secara lokal setelah aktivasi satu kali, menjadikannya aman namun tetap fungsional secara offline.
-   **Pengiriman Lisensi Otomatis**: Alur langganan mandiri di mana pengguna dapat mengirimkan bukti pembayaran, dan lisensi akan dikirim serta diaktivasi secara otomatis melalui sistem *heartbeat* yang aman.
-   **Integrasi Perangkat Keras**: Mendukung pemindai barcode (baik berbasis kamera maupun hardware eksternal) serta pencetakan struk thermal melalui API cetak browser.
-   **Panel Admin Berfitur Lengkap**: Bagian sisi server yang aman bagi administrator untuk mengelola pelanggan, lisensi, paket langganan, serta memantau riwayat pembayaran dan sesi pengguna yang sedang online.
-   **Laporan Mendalam**: Menyediakan laporan mendetail untuk penjualan, inventaris, pergerakan stok, dan konsumsi bahan baku, dengan opsi ekspor ke Excel dan PDF.

## 🚀 Rilis Terbaru (v0.3.1) - Manajemen Konsinyasi / Titipan

Pembaruan versi **v0.3.1** memperkenalkan dukungan penuh untuk **Produk Konsinyasi (Titipan Pihak Ketiga)**, memberikan kemampuan bagi pemilik toko untuk bermitra dengan pemasok luar secara akurat, andal, dan mudah dikelola bahkan untuk skema operasional harian (*daily resetting items*).

Beberapa perubahan dan penambahan utama meliputi:

-   **Skema Komisi Fleksibel**: Mendukung bagi hasil berdasarkan **Persentase (%)** dari nilai jual atau **Flat / Nominal Tetap (Rp)** per unit item yang berhasil terjual.
-   **Manajemen Form Produk Pintar**: Menghilangkan kolom Harga Modal (*cost price*) secara dinamis pada produk yang ditandai sebagai konsinyasi untuk mencegah tumpang tindih data, serta membersihkan nilai modal secara otomatis saat formulir disimpan.
-   **Buku Laporan Bagi Hasil Dedicated**: Menyediakan halaman laporan khusus konsinyasi untuk mengaudit jumlah barang masuk (pagi), barang terjual (siang), sisa barang ditarik kembali oleh penitip (sore), komisi yang berhak disimpan toko, serta nominal total siap bayar ke penitip.
-   **Pemisahan HPP & Liabilitas Titipan**: Menyempurnakan Laporan Penjualan dan Audit Laba & Kas dengan memisahkan nilai aset HPP toko dari kewajiban biaya bagi hasil konsinyasi. Hal ini menjaga keakuratan analisis margin keuntungan riil toko Anda tanpa distorsi angka modal.
-   **Antarmuka Kasir Informatif**: Menambahkan penanda (*badge*) visual bertuliskan "Titipan" serta nama penitip pada baris keranjang kasir (*Classic & Default Cashier*) dan modal riwayat transaksi sif untuk memudahkan identifikasi oleh operator kasir.
-   **Ekspor Dokumen yang Diperbarui**: Fungsi ekspor laporan penjualan dan audit ke Excel (.xlsx) & PDF (.pdf) kini mendukung visualisasi kolom HPP Standar, Bagi Hasil Titipan, Pajak, dan Laba Bersih secara terpisah.
