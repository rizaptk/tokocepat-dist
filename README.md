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
