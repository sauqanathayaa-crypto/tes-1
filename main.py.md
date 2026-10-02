# ==========================================
# SMART LAUNDRY
# ==========================================

# Membuat / membuka database
koneksi = sqlite3.connect("smart_laundry.db")
cursor = koneksi.cursor()

# ==========================================
# MEMBUAT TABEL
# ==========================================

cursor.execute("""
CREATE TABLE IF NOT EXISTS pelanggan (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    nama TEXT NOT NULL,
    no_hp TEXT NOT NULL
)
""")

cursor.execute("""
CREATE TABLE IF NOT EXISTS transaksi (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    id_pelanggan INTEGER,
    jenis_layanan TEXT,
    berat REAL,
    harga REAL,
    status TEXT,
    tanggal_masuk TEXT,
    tanggal_selesai TEXT,
    FOREIGN KEY (id_pelanggan) REFERENCES pelanggan(id)
)
""")

koneksi.commit()


# ==========================================
# TAMBAH PELANGGAN
# ==========================================

def tambah_pelanggan():
    print("\n===== TAMBAH PELANGGAN =====")

    nama = input("Nama pelanggan : ")
    no_hp = input("No. HP          : ")

    cursor.execute("""
        INSERT INTO pelanggan (nama, no_hp)
        VALUES (?, ?)
    """, (nama, no_hp))

    koneksi.commit()

    print("\nPelanggan berhasil ditambahkan!")


# ==========================================
# MENAMPILKAN PELANGGAN
# ==========================================

def tampilkan_pelanggan():
    cursor.execute("SELECT * FROM pelanggan")
    data = cursor.fetchall()

    print("\n===== DATA PELANGGAN =====")

    if not data:
        print("Belum ada data pelanggan.")
        return

    for pelanggan in data:
        print(
            f"ID: {pelanggan[0]} | "
            f"Nama: {pelanggan[1]} | "
            f"No HP: {pelanggan[2]}"
        )


# ==========================================
# MEMILIH LAYANAN
# ==========================================

def pilih_layanan():
    print("\n===== PILIH LAYANAN =====")
    print("1. Cuci Kering  - Rp8.000/kg")
    print("2. Cuci Setrika  - Rp10.000/kg")
    print("3. Setrika       - Rp6.000/kg")

    pilihan = input("Pilih layanan (1/2/3): ")

    if pilihan == "1":
        return "Cuci Kering", 8000
    elif pilihan == "2":
        return "Cuci Setrika", 10000
    elif pilihan == "3":
        return "Setrika", 6000
    else:
        print("Pilihan tidak tersedia.")
        return None, 0


# ==========================================
# PROSES TRANSAKSI
# ==========================================

def proses_transaksi():

    print("\n===== PROSES TRANSAKSI =====")

    # Menampilkan pelanggan
    tampilkan_pelanggan()

    try:
        id_pelanggan = int(input("\nMasukkan ID pelanggan: "))
    except ValueError:
        print("ID harus berupa angka.")
        return

    # Mengecek pelanggan
    cursor.execute(
        "SELECT * FROM pelanggan WHERE id = ?",
        (id_pelanggan,)
    )

    pelanggan = cursor.fetchone()

    if pelanggan is None:
        print("Pelanggan tidak ditemukan.")
        return

    # Memilih layanan
    jenis_layanan, harga_per_kg = pilih_layanan()

    if jenis_layanan is None:
        return

    # Input berat
    try:
        berat = float(input("Berat pakaian (kg): "))
    except ValueError:
        print("Berat harus berupa angka.")
        return

    # Menghitung harga
    total_harga = berat * harga_per_kg

    print("\n===== DETAIL TRANSAKSI =====")
    print("Pelanggan     :", pelanggan[1])
    print("Layanan       :", jenis_layanan)
    print("Berat         :", berat, "kg")
    print("Harga per kg  : Rp", harga_per_kg)
    print("Total harga   : Rp", total_harga)

    # Tanggal masuk
    tanggal_masuk = datetime.now().strftime("%Y-%m-%d %H:%M:%S")

    # Menyimpan transaksi
    cursor.execute("""
        INSERT INTO transaksi
        (id_pelanggan, jenis_layanan, berat, harga,
         status, tanggal_masuk, tanggal_selesai)
        VALUES (?, ?, ?, ?, ?, ?, ?)
    """, (
        id_pelanggan,
        jenis_layanan,
        berat,
        total_harga,
        "Diproses",
        tanggal_masuk,
        "-"
    ))

    koneksi.commit()

    print("\nTransaksi berhasil disimpan!")


# ==========================================
# MELIHAT DATA TRANSAKSI
# ==========================================

def lihat_transaksi():

    print("\n===== DATA TRANSAKSI =====")

    cursor.execute("""
        SELECT 
            transaksi.id,
            pelanggan.nama,
            transaksi.jenis_layanan,
            transaksi.berat,
            transaksi.harga,
            transaksi.status,
            transaksi.tanggal_masuk,
            transaksi.tanggal_selesai
        FROM transaksi
        JOIN pelanggan
        ON transaksi.id_pelanggan = pelanggan.id
    """)

    data = cursor.fetchall()

    if not data:
        print("Belum ada transaksi.")
        return

    for transaksi in data:

        print("\n-----------------------------")
        print("ID Transaksi :", transaksi[0])
        print("Pelanggan    :", transaksi[1])
        print("Layanan      :", transaksi[2])
        print("Berat        :", transaksi[3], "kg")
        print("Harga        : Rp", transaksi[4])
        print("Status       :", transaksi[5])
        print("Tanggal Masuk:", transaksi[6])
        print("Selesai      :", transaksi[7])


# ==========================================
# MENU UTAMA
# ==========================================

def menu_utama():

    while True:

        print("\n")
        print("================================")
        print("       SMART LAUNDRY")
        print("================================")
        print("1. Tambah Pelanggan")
        print("2. Proses Transaksi")
        print("3. Lihat Data Transaksi")
        print("4. Keluar")
        print("================================")

        pilihan = input("Pilih menu: ")

        if pilihan == "1":
            tambah_pelanggan()

        elif pilihan == "2":
            proses_transaksi()

        elif pilihan == "3":
            lihat_transaksi()

        elif pilihan == "4":
            print("\nTerima kasih telah menggunakan")
            print("SMART LAUNDRY.")
            break

        else:
            print("\nPilihan menu tidak tersedia.")


# ==========================================
# MENJALANKAN PROGRAM
# ==========================================

if __name__ == "__main__":
    menu_utama()

# Menutup database
koneksi.close()
