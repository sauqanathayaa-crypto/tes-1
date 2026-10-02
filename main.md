# 🏛️ Dokumen Desain & Arsitektur Sistem - Smart Laundry
**Sistem Digital Twin Pemantauan Mesin Cuci dan Kapasitas Ruang Secara Real-Time**

---

## 1. Arsitektur Sistem (System Architecture)
Arsitektur sistem Smart Laundry ini dirancang menggunakan konsep tiga lapis (*3-Tier Architecture*) yang memisahkan antara antarmuka pengguna, logika server, dan penyimpanan data.

```mermaid
graph TD
    %% Styling
    classDef client fill:#DB7093,stroke:#333,stroke-width:2px,color:#fff;
    classDef server fill:#556B2F,stroke:#333,stroke-width:2px,color:#fff;
    classDef db fill:#4682B4,stroke:#333,stroke-width:2px,color:#fff;

    A[Browser Pengguna / Web Dashboard<br>HTML5, CSS3, JavaScript] -->|HTTP Request / WebSocket| B[Backend Server<br>Python Flask API]
    B -->|Query / Simpan Data| C[(Database Utama<br>SQLite / MySQL)]
    B -->|Ambil Data Sensor Mesin| D[Modul Simulasi / Perangkat IoT Mesin Cuci]

    class A client;
    class B server;
    class C,D db;


        datetime timestamp
    }

    USER ||--o{ TRANSACTION : "melakukan"
    MACHINE ||--o{ TRANSACTION : "digunakan_dalam"
