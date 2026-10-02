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

graph TD
    Start([Mulai]) --> Input[Pengguna Mengakses Halaman Web]
    Input --> Request[Kirim Permintaan Data ke Server]
    Request --> Check{Cek Status Mesin & Ruangan}
    
    Check -->|Data Diperbarui| Fetch[(Ambil Data dari Database)]
    Fetch --> Process[Server Memproses Status & Timer]
    
    Process --> Render[Kirim Data JSON ke Frontend]
    Render --> Display[Dashboard Menampilkan Status Real-Time]
    
    Display --> End([Selesai / Menunggu Update Berikutnya])

erDiagram
    USER {
        int id PK
        string username
        string password
        string role
    }

    MACHINE {
        int id PK
        string machine_name
        string status
        int remaining_time
    }

    ROOM_CAPACITY {
        int id PK
        int total_visitors
        string density_status
        datetime updated_at
    }

    TRANSACTION {
        int id PK
        int user_id FK
        int machine_id FK
        string duration_package
        datetime timestamp
    }

    USER ||--o{ TRANSACTION : "melakukan"
    MACHINE ||--o{ TRANSACTION : "digunakan_dalam"
