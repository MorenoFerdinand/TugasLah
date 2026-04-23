# 🚗 Data Warehouse – Large Cars Dataset
**UTS Business Intelligence | Kelompok 07**

---

## 👥 Anggota Kelompok

| Nama | NIM |
|------|-----|
| Nabil Daffa Atalasyah | 2409116090 |
| Moreno Ferdinand Farhantino | 2409116097 |
| Reswara Ganendra Rashi Dewa | 2409116100 |
| Muhammad Arifin Alqi. AB | 2409116116 |

---

## 📋 Deskripsi Proyek

Proyek ini membangun sebuah **Data Warehouse** berbasis dataset publik **Large Cars Dataset** yang berisi 428 model kendaraan dari 38 merek otomotif. Dataset mencakup informasi harga, spesifikasi mesin, efisiensi bahan bakar, dan dimensi fisik kendaraan dari 3 region utama: Asia, Europe, dan USA.

Data warehouse dirancang menggunakan **Star Schema** dengan 1 tabel fakta dan 3 tabel dimensi, kemudian dilakukan analisis data untuk menghasilkan insight industri otomotif.

---

## 📁 Struktur Repository

```
UTS-Business-Intelligence/
├── dataset/
│   └── Large_Cars_Dataset.csv
├── data_warehouse/
│   ├── dim_brand.csv
│   ├── dim_vehicle_class.csv
│   ├── dim_drivetrain.csv
│   └── fact_cars.csv
├── Business_Intelligence.ipynb
├── Laporan_Business_Intelligence_Kelompok_7.docx
└── README.md
```

---

## 🏗️ Desain Star Schema

<img width="2779" height="1979" alt="star_schema_diagram" src="https://github.com/user-attachments/assets/9ed52344-bdfa-492b-b2c9-b31e7deb54e8" />


### Tabel Dimensi
| Tabel | Kolom Utama | Jumlah Baris |
|-------|-------------|--------------|
| dim_brand | brand_id, Brand, Region | 38 |
| dim_vehicle_class | class_id, VehicleClass | 6 |
| dim_drivetrain | drive_id, DriveTrain | 3 |

### Tabel Fakta
| Tabel | Kolom Utama | Jumlah Baris |
|-------|-------------|--------------|
| fact_cars | car_id, brand_id, class_id, drive_id, MSRP, DealerCost, HorsePower, MPG_City, MPG_Highway, Weight, Wheelbase, Length | 428 |

---

## ⚙️ Proses ETL

### Extract
- Sumber data: `Large_Cars_Dataset.csv`
- Tools: Python, Pandas
- Hasil: 428 baris × 15 kolom

### Transform
- Konversi kolom `MSRP` dan `DealerCost` dari string (`$36,945`) ke integer
- Penanganan missing value pada kolom `Cylinders` (2 baris Mazda RX-8, mesin rotary) → diisi `0`
- Trim whitespace pada seluruh kolom bertipe string
- Pembuatan 3 tabel dimensi dengan surrogate key
- Pembentukan tabel fakta `fact_cars` via merge

### Load
- Output: 4 file CSV tersimpan di folder `data_warehouse/`
- Validasi: semua foreign key terisi, tidak ada nilai null

---

## 📊 Analisis Data

| # | Pertanyaan | Jenis Chart |
|---|-----------|-------------|
| 1 | Brand mana yang memiliki rata-rata harga tertinggi? | Horizontal Bar Chart |
| 2 | Kelas kendaraan mana yang paling efisien bahan bakar? | Grouped Bar Chart |
| 3 | Region mana yang paling banyak memproduksi model? | Pie Chart |
| 4 | Jenis penggerak mana yang memiliki rata-rata harga tertinggi? | Bar Chart |
| 5 | Apakah HP tinggi berkorelasi dengan harga mahal? | Scatter Plot |
| 6 | Region mana yang memproduksi kendaraan bertenaga tertinggi? | Bar Chart |

### Temuan Utama
- 🏆 **Porsche** memiliki rata-rata harga tertinggi ($83.565), diikuti Jaguar dan Mercedes-Benz
- 🌿 Kelas **Hybrid** paling efisien dengan rata-rata 55 MPG (kota) dan 56 MPG (highway)
- 🌏 **Asia** mendominasi jumlah model (158 model, 36,9%), namun **Eropa** unggul di harga dan tenaga kuda
- 🔁 Kendaraan **RWD** memiliki rata-rata harga tertinggi ($46.094)
- 📈 Terdapat **korelasi positif** antara HorsePower dan MSRP

---

## 🔗 Link

- 📓 **Google Colab**: [Business_Intelegent.ipynb](https://colab.research.google.com/drive/1pYJQZshXYFlXC7R6C_FbFNc_c7k1S_rQ)
- 📄 **Laporan**: tersedia di repository

---

## 🛠️ Tools & Library

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Pandas](https://img.shields.io/badge/Pandas-Latest-green)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Latest-orange)
![SQLite](https://img.shields.io/badge/SQLite-Latest-lightgrey)
![Google Colab](https://img.shields.io/badge/Google%20Colab-Notebook-yellow)
