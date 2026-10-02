# Rancangan UX/UI - Smart Laundry

## 1. Deskripsi

Smart Laundry merupakan aplikasi yang digunakan untuk mengelola data pelanggan, transaksi laundry, status laundry, dan pemantauan proses laundry.

Rancangan UX/UI dibuat agar pengguna dapat menggunakan aplikasi dengan mudah, sederhana, dan jelas.

---

# 2. Alur Navigasi Aplikasi

```mermaid
flowchart TD

    A["Splash Screen"] --> B["Login"]
    B --> C["Menu Utama"]

    C --> D["Tambah Pelanggan"]
    C --> E["Proses Transaksi"]
    C --> F["Data Transaksi"]
    C --> G["Status Laundry"]
    C --> H["Profil"]
    C --> I["Keluar"]

    D --> D1["Input Nama"]
    D1 --> D2["Input No HP"]
    D2 --> D3["Simpan Data"]
    D3 --> C

    E --> E1["Pilih Pelanggan"]
    E1 --> E2["Pilih Layanan"]
    E2 --> E3["Input Berat"]
    E3 --> E4["Hitung Harga"]
    E4 --> E5["Simpan Transaksi"]
    E5 --> C

    F --> F1["Pilih Transaksi"]
    F1 --> F2["Detail Transaksi"]
    F2 --> C

    G --> G1["Lihat Status Mesin"]
    G1 --> G2["Lihat Kapasitas"]
    G2 --> C

    H --> H1["Data Pengguna"]
    H1 --> H2["Pengaturan"]
    H2 --> C

    I --> J["Konfirmasi Keluar"]
    J --> K["Selesai"]
