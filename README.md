# 2.1 Rancangan UX/UI - Smart Laundry

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

```
# 2.2 Rancangan Sistem

## 1. Arsitektur Sistem

```mermaid
flowchart TD

    USER["Pengguna"]
    UI["Interface / Aplikasi Smart Laundry"]
    INPUT["Input / Output"]
    LOGIC["Logika Aplikasi"]
    PROCESS["Pengolahan Data"]
    DB[("Database")]

    USER --> UI
    UI <--> INPUT
    UI --> LOGIC
    LOGIC --> PROCESS
    PROCESS <--> DB
```

---

## 2. Flowchart Sistem

```mermaid
flowchart TD

    START(["Mulai"])
    MENU["Tampilkan Menu Utama"]
    PILIH{"Pilih Menu"}

    TAMBAH["Tambah Pelanggan"]
    TRANSAKSI["Proses Transaksi"]
    DATA["Lihat Data Transaksi"]
    KELUAR["Keluar"]

    INPUT1["Input Nama dan No HP"]
    SIMPAN1["Simpan Data Pelanggan"]

    PILIHPEL["Pilih Pelanggan"]
    LAYANAN["Pilih Layanan Laundry"]
    BERAT["Input Berat Pakaian"]
    HARGA["Hitung Harga"]
    SIMPAN2["Simpan Transaksi"]

    DATABASE[("Database")]

    START --> MENU
    MENU --> PILIH

    PILIH --> TAMBAH
    PILIH --> TRANSAKSI
    PILIH --> DATA
    PILIH --> KELUAR

    TAMBAH --> INPUT1
    INPUT1 --> SIMPAN1
    SIMPAN1 --> DATABASE
    DATABASE --> MENU

    TRANSAKSI --> PILIHPEL
    PILIHPEL --> LAYANAN
    LAYANAN --> BERAT
    BERAT --> HARGA
    HARGA --> SIMPAN2
    SIMPAN2 --> DATABASE
    DATABASE --> MENU

    DATA --> DATABASE
    DATABASE --> MENU

    KELUAR --> SELESAI(["Selesai"])
```

---

## 3. ERD / Struktur Database

```mermaid
erDiagram

    PELANGGAN ||--o{ TRANSAKSI : memiliki

    PELANGGAN {
        int id PK
        string nama
        string no_hp
    }

    TRANSAKSI {
        int id PK
        int id_pelanggan FK
        string jenis_layanan
        float berat
        float harga
        string status
        string tanggal_masuk
        string tanggal_selesai
    }
```

---
