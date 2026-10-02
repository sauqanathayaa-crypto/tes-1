2. Dokumen Desain & Arsitektur

• Rancangan UX/UI

Rancangan UX/UI aplikasi Digital Twin Smart Laundry dibuat dalam bentuk dashboard monitoring untuk memudahkan pengguna dalam memantau kondisi mesin laundry secara real-time.

Tampilan utama terdiri dari:

Dashboard – menampilkan kondisi seluruh mesin.

Status Mesin – menunjukkan mesin sedang mencuci, mengeringkan, selesai, atau tidak digunakan.

Data Sensor – menampilkan suhu, kelembapan, penggunaan listrik, dan waktu proses.

Digital Twin – menampilkan representasi virtual mesin laundry.

Monitoring – menampilkan perubahan kondisi mesin secara real-time.

Kontrol Mesin – memungkinkan operator mengaktifkan atau menonaktifkan mesin.

Riwayat Aktivitas – menyimpan aktivitas penggunaan mesin.

┌────────────────────────────────────────────────────┐
│        DIGITAL TWIN SMART LAUNDRY                  │
│        Monitoring & Management System              │
├────────────────────────────────────────────────────┤
│                                                    │
│  Mesin Cuci       Mesin Pengering     Antrian      │
│    2 / 3              1 / 2             5          │
│                                                    │
├────────────────────────────────────────────────────┤
│ STATUS MESIN                                       │
│                                                    │
│ ┌──────────────┐  ┌──────────────┐  ┌───────────┐ │
│ │ 🧺 Cuci 01   │  │ 🧺 Cuci 02   │  │ Pengering │ │
│ │              │  │              │  │           │ │
│ │ ● MENCUCI    │  │ ● SELESAI    │  │ ● OFF     │ │
│ │ Suhu: 28°C   │  │ Suhu: 27°C   │  │ Suhu:32°C │ │
│ │ Air: 65%     │  │ Air: 40%     │  │ RH: 45%   │ │
│ │              │  │              │  │           │ │
│ │ [ ON ] [OFF] │  │ [ ON ] [OFF] │  │[ON] [OFF] │ │
│ └──────────────┘  └──────────────┘  └───────────┘ │
│                                                    │
├────────────────────────────────────────────────────┤
│             DIGITAL TWIN                           │
│                                                    │
│        ┌─────────┐       ┌─────────┐              │
│        │ 🧺      │       │ ♨️      │              │
│        │ CUCI    │       │ KERING  │              │
│        └─────────┘       └─────────┘              │
│                                                    │
├────────────────────────────────────────────────────┤
│ Aktivitas Terbaru                                  │
│ ● Mesin Cuci 01 mulai mencuci                      │
│ ● Data sensor diperbarui                           │
│ ● Pengering 01 selesai digunakan                   │
└────────────────────────────────────────────────────┘


• Rancangan Sistem

Rancangan sistem Digital Twin Smart Laundry terdiri dari beberapa diagram pendukung awal, yaitu Flowchart, Arsitektur Sistem, dan ERD.

1. Flowchart Alur Data

┌───────────┐
              │   MULAI   │
              └─────┬─────┘
                    ↓
        ┌─────────────────────┐
        │ Sensor membaca data │
        │ suhu & kelembapan   │
        └──────────┬──────────┘
                   ↓
        ┌─────────────────────┐
        │ ESP32 menerima data │
        └──────────┬──────────┘
                   ↓
        ┌─────────────────────┐
        │ Backend menerima &  │
        │ menyimpan data      │
        └──────────┬──────────┘
                   ↓
        ┌─────────────────────┐
        │ Digital Twin        │
        │ memperbarui status  │
        │ mesin                │
        └──────────┬──────────┘
                   ↓
        ┌─────────────────────┐
        │ Dashboard            │
        │ menampilkan data     │
        │ secara real-time     │
        └──────────┬──────────┘
                   ↓
          ┌─────────────────┐
          │ Pengguna ingin  │
          │ mengontrol mesin│
          └────────┬────────┘
                   ↓
              ┌────┴────┐
              │   Ya    │
              └────┬────┘
                   ↓
        ┌─────────────────────┐
        │ Kirim perintah      │
        │ ON / OFF            │
        └──────────┬──────────┘
                   ↓
        ┌─────────────────────┐
        │ ESP32 menjalankan   │
        │ perintah mesin      │
        └──────────┬──────────┘
                   ↓
              ┌───────────┐
              │  SELESAI  │
              └───────────┘

2. Arsitektur Sistem

┌──────────────────┐
│   MESIN LAUNDRY  │
│                  │
│ Mesin Cuci       │
│ Mesin Pengering  │
│ Sensor           │
└────────┬─────────┘
         │
         │ Data Sensor
         ↓
┌──────────────────┐
│      ESP32       │
│   IoT Gateway    │
└────────┬─────────┘
         │
         │ Internet
         ↓
┌──────────────────┐
│     BACKEND      │
│   API / Server   │
└────────┬─────────┘
         │
    ┌────┴─────┐
    ↓          ↓
┌─────────┐ ┌──────────────┐
│Database │ │ Digital Twin │
└────┬────┘ └──────┬───────┘
     │             │
     └──────┬──────┘
            ↓
┌──────────────────────┐
│      DASHBOARD       │
│                      │
│ Admin / Operator     │
│ Monitoring Real-time │
└──────────────────────┘

3. ERD / Struktur Database

Database dapat dibuat dengan beberapa tabel utama:

┌──────────────────────┐
│       USERS          │
├──────────────────────┤
│ id_user       PK     │
│ nama                 │
│ email                │
│ password             │
│ role                 │
└──────────┬───────────┘
           │
           │ 1
           │
           │ N
┌──────────▼───────────┐
│       MESIN          │
├──────────────────────┤
│ id_mesin       PK    │
│ nama_mesin           │
│ jenis_mesin          │
│ status               │
│ kapasitas            │
│ lokasi               │
└──────────┬───────────┘
           │
           │ 1
           │
           │ N
┌──────────▼───────────┐
│     DATA_SENSOR      │
├──────────────────────┤
│ id_sensor      PK    │
│ id_mesin       FK    │
│ suhu                 │
│ kelembapan           │
│ daya_listrik         │
│ waktu                │
└──────────────────────┘


┌──────────────────────┐
│      PELANGGAN       │
├──────────────────────┤
│ id_pelanggan   PK    │
│ nama                 │
│ no_hp                │
│ alamat               │
└──────────┬───────────┘
           │
           │ 1
           │
           │ N
┌──────────▼───────────┐
│      TRANSAKSI       │
├──────────────────────┤
│ id_transaksi   PK    │
│ id_pelanggan   FK    │
│ id_mesin       FK    │
│ layanan              │
│ total_harga          │
│ tanggal              │
│ status               │
└──────────────────────┘
