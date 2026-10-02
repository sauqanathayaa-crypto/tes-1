<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Digital Twin Smart Laundry</title>

    <link rel="stylesheet" href="style.css">
</head>

<body>

    <!-- HEADER -->
    <header>
        <div class="header-content">
            <h1>🔗 DIGITAL TWIN SMART LAUNDRY</h1>
            <p>Project Setup & System Architecture</p>
        </div>
    </header>


    <main>

        <!-- ================================================= -->
        <!-- 1. FLOWCHART -->
        <!-- ================================================= -->

        <section class="section">

            <h2>🔗 1. Flowchart Alur Data</h2>

            <div class="flowchart">

                <div class="flow start">
                    MULAI
                </div>

                <div class="arrow">↓</div>


                <div class="flow process">
                    <b>Sensor membaca data</b>

                    <p>
                        Suhu, kelembapan,
                        arus listrik dan status mesin
                    </p>
                </div>

                <div class="arrow">↓</div>


                <div class="flow process">
                    <b>ESP32 menerima data</b>

                    <p>
                        ESP32 mengirim data
                        melalui WiFi
                    </p>
                </div>

                <div class="arrow">↓</div>


                <div class="flow process">
                    <b>Backend / API</b>

                    <p>
                        Menerima data dan
                        menyimpannya ke database
                    </p>
                </div>

                <div class="arrow">↓</div>


                <div class="flow process">
                    <b>Digital Twin diperbarui</b>

                    <p>
                        Sistem memperbarui
                        kondisi virtual mesin
                    </p>
                </div>

                <div class="arrow">↓</div>


                <div class="flow process">
                    <b>Dashboard</b>

                    <p>
                        Menampilkan data
                        secara real-time
                    </p>
                </div>

                <div class="arrow">↓</div>


                <div class="flow decision">
                    Apakah pengguna ingin
                    mengontrol mesin?
                </div>


                <div class="decision-area">

                    <div class="branch">
                        <span>TIDAK</span>

                        <div class="arrow">
                            ↩
                        </div>

                        <small>
                            Kembali ke monitoring
                        </small>
                    </div>


                    <div class="branch yes">

                        <span>YA</span>

                        <div class="arrow">
                            ↓
                        </div>

                        <div class="flow process small">
                            Kirim perintah
                            ON / OFF ke ESP32
                        </div>

                        <div class="arrow">
                            ↓
                        </div>

                        <div class="flow process small">
                            ESP32 menjalankan
                            perintah mesin
                        </div>

                    </div>

                </div>


                <div class="arrow">↓</div>

                <div class="flow finish">
                    SELESAI
                </div>

            </div>

        </section>


        <!-- ================================================= -->
        <!-- 2. ARSITEKTUR SISTEM -->
        <!-- ================================================= -->

        <section class="section">

            <h2>🔗 2. Arsitektur Sistem</h2>


            <!-- LAYER IOT -->

            <div class="layer">

                <h3>Layer Perangkat / IoT</h3>

                <div class="architecture">

                    <div class="system-box">

                        <div class="icon">
                            🧺
                        </div>

                        <h4>Mesin Cuci</h4>

                        <p>
                            Mesin + Aktuator
                        </p>

                    </div>


                    <div class="system-box">

                        <div class="icon">
                            ♨️
                        </div>

                        <h4>Mesin Pengering</h4>

                        <p>
                            Mesin + Aktuator
                        </p>

                    </div>


                    <div class="system-box">

                        <div class="icon">
                            🌡️
                        </div>

                        <h4>Sensor</h4>

                        <p>
                            Suhu<br>
                            Kelembapan<br>
                            Arus listrik
                        </p>

                    </div>


                    <div class="system-box esp">

                        <div class="icon">
                            🔌
                        </div>

                        <h4>ESP32</h4>

                        <p>
                            IoT Gateway
                        </p>

                    </div>

                </div>

            </div>


            <div class="connection">
                ↓ WiFi / Internet ↓
            </div>


            <!-- SERVER -->

            <div class="layer">

                <h3>Layer Server & Data</h3>

                <div class="architecture">

                    <div class="system-box">

                        <div class="icon">
                            ☁️
                        </div>

                        <h4>Backend / API</h4>

                        <p>
                            Node.js / Laravel / Python
                        </p>

                    </div>


                    <div class="system-box">

                        <div class="icon">
                            🗄️
                        </div>

                        <h4>Database</h4>

                        <p>
                            MySQL / PostgreSQL
                        </p>

                    </div>

                </div>

            </div>


            <div class="connection">
                ↓
            </div>


            <!-- APPLICATION -->

            <div class="layer">

                <h3>Layer Aplikasi / User Interface</h3>

                <div class="architecture">

                    <div class="system-box">

                        <div class="icon">
                            🖥️
                        </div>

                        <h4>Dashboard</h4>

                        <p>
                            Monitoring<br>
                            Kontrol Mesin<br>
                            Riwayat
                        </p>

                    </div>


                    <div class="system-box">

                        <div class="icon">
                            🧺
                        </div>

                        <h4>Digital Twin</h4>

                        <p>
                            Visualisasi virtual
                            kondisi mesin
                        </p>

                    </div>

                </div>

            </div>


            <div class="connection">
                ↓
            </div>


            <!-- USER -->

            <div class="layer">

                <h3>Pengguna</h3>

                <div class="architecture">

                    <div class="system-box">

                        <div class="icon">
                            👨‍💻
                        </div>

                        <h4>Operator</h4>

                        <p>
                            Monitoring
                            dan kontrol
                        </p>

                    </div>


                    <div class="system-box">

                        <div class="icon">
                            ⚙️
                        </div>

                        <h4>Admin</h4>

                        <p>
                            Manajemen data
                        </p>

                    </div>


                    <div class="system-box">

                        <div class="icon">
                            👥
                        </div>

                        <h4>Pelanggan</h4>

                        <p>
                            Layanan dan antrian
                        </p>

                    </div>

                </div>

            </div>

        </section>


        <!-- ================================================= -->
        <!-- 3. ERD -->
        <!-- ================================================= -->

        <section class="section">

            <h2>🔗 3. ERD / Struktur Database</h2>


            <div class="erd-container">


                <!-- USERS -->

                <div class="table users">

                    <div class="table-title">
                        users
                    </div>

                    <ul>

                        <li>
                            🔑 <b>id_user</b> (PK)
                        </li>

                        <li>
                            nama
                        </li>

                        <li>
                            email
                        </li>

                        <li>
                            password
                        </li>

                        <li>
                            role
                        </li>

                        <li>
                            created_at
                        </li>

                    </ul>

                </div>


                <div class="relation">
                    1 ───── N
                    <br>
                    <small>melakukan</small>
                </div>


                <!-- TRANSAKSI -->

                <div class="table transaksi">

                    <div class="table-title">
                        transaksi
                    </div>

                    <ul>

                        <li>
                            🔑 <b>id_transaksi</b> (PK)
                        </li>

                        <li>
                            🔗 id_pelanggan (FK)
                        </li>

                        <li>
                            🔗 id_mesin (FK)
                        </li>

                        <li>
                            jenis_layanan
                        </li>

                        <li>
                            total_harga
                        </li>

                        <li>
                            tanggal
                        </li>

                        <li>
                            status
                        </li>

                    </ul>

                </div>


                <!-- PELANGGAN -->

                <div class="table pelanggan">

                    <div class="table-title">
                        pelanggan
                    </div>

                    <ul>

                        <li>
                            🔑 <b>id_pelanggan</b> (PK)
                        </li>

                        <li>
                            nama
                        </li>

                        <li>
                            no_hp
                        </li>

                        <li>
                            alamat
                        </li>

                        <li>
                            created_at
                        </li>

                    </ul>

                </div>


                <div class="relation">
                    1 ───── N
                    <br>
                    <small>menggunakan</small>
                </div>


                <!-- MESIN -->

                <div class="table mesin">

                    <div class="table-title">
                        mesin
                    </div>

                    <ul>

                        <li>
                            🔑 <b>id_mesin</b> (PK)
                        </li>

                        <li>
                            nama_mesin
                        </li>

                        <li>
                            jenis_mesin
                        </li>

                        <li>
                            kapasitas
                        </li>

                        <li>
                            lokasi
                        </li>

                        <li>
                            status
                        </li>

                    </ul>

                </div>


                <!-- SENSOR -->

                <div class="table sensor">

                    <div class="table-title">
                        data_sensor
                    </div>

                    <ul>

                        <li>
                            🔑 <b>id_sensor</b> (PK)
                        </li>

                        <li>
                            🔗 id_mesin (FK)
                        </li>

                        <li>
                            suhu
                        </li>

                        <li>
                            kelembapan
                        </li>

                        <li>
                            arus_listrik
                        </li>

                        <li>
                            waktu
                        </li>

                    </ul>

                </div>


                <div class="relation">
                    1 ───── N
                    <br>
                    <small>memiliki data</small>
                </div>


                <!-- LOG -->

                <div class="table log">

                    <div class="table-title">
                        log_aktivitas
                    </div>

                    <ul>

                        <li>
                            🔑 <b>id_log</b> (PK)
                        </li>

                        <li>
                            🔗 id_user (FK)
                        </li>

                        <li>
                            aktivitas
                        </li>

                        <li>
                            waktu
                        </li>

                    </ul>

                </div>

            </div>


            <div class="legend">

                <b>Keterangan:</b>

                <span>
                    🔑 PK = Primary Key
                </span>

                <span>
                    🔗 FK = Foreign Key
                </span>

                <span>
                    1 = Satu
                </span>

                <span>
                    N = Banyak
                </span>

            </div>

        </section>

    </main>


    <footer>

        <p>
            Digital Twin Smart Laundry © 2026
        </p>

    </footer>


    <script src="script.js"></script>

</body>
</html>
