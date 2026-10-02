# 🔄 Diagram Alur Sistem (Flowchart) - Smart Laundry
**Sistem Digital Twin Pemantauan Mesin Cuci dan Kapasitas Ruang**

Berikut adalah rancangan alur kerja sistem (*System Flowchart*) dari aplikasi Smart Laundry:

---

```mermaid
graph TD
    %% Styling Node
    classDef startEnd fill:#DB7093,stroke:#333,stroke-width:2px,color:#fff;
    classDef process fill:#556B2F,stroke:#333,stroke-width:2px,color:#fff;
    classDef decision fill:#D2B48C,stroke:#333,stroke-width:2px,color:#000;
    classDef database fill:#4682B4,stroke:#333,stroke-width:2px,color:#fff;

    %% Alur Diagram Flowchart
    A([Mulai]) --> B[Pengguna Membuka Web Dashboard]
    B --> C{Pilih Menu}
    
    C -->|Status Mesin| D[Sistem Mengambil Data Sensor / Status Mesin]
    C -->|Kapasitas Ruang| E[Sistem Menghitung Tingkat Kepadatan Pengunjung]
    
    D --> F[(Database Status Mesin)]
    E --> G[(Database Ruang Tunggu)]
    
    F --> H[Tampilkan Kondisi Mesin Real-Time:<br> Aktif / Standby / Selesai]
    G --> H
    
    H --> I{Apakah Proses Cuci Selesai?}
    
    I -->|Ya| J[Kirim Notifikasi / Update Tampilan Selesai]
    I -->|Tidak| K[Perbarui Timer Hitung Mundur Sisa Waktu]
    
    J --> L([Selesai])
    K --> B
    
    %% Terapkan Style
    class A,L startEnd;
    class B,D,E,H,J,K process;
    class C,I decision;
    class F,G database;
