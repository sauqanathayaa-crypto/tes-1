# Dokumen Desain & Arsitektur Sistem - Smart Laundry

## Sistem Digital Twin Pemantauan Mesin Cuci dan Kapasitas Ruang Secara Real-Time

---

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

## 4. Struktur Sistem

```text
Pengguna
   |
   v
Interface Smart Laundry
   |
   v
Logika Aplikasi
   |
   v
Pengolahan Data
   |
   v
Database
```

---

## 5. Fitur Sistem

- Tambah pelanggan
- Menampilkan pelanggan
- Memilih layanan laundry
- Menginput berat pakaian
- Menghitung harga
- Menyimpan transaksi
- Melihat data transaksi
- Menampilkan status laundry

---

## 6. Teknologi

- Python
- SQLite
- Visual Studio Code
- GitHub
- Mermaid Diagram
