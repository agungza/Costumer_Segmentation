# 🧩 Customer Segmentation with K-Means Clustering

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0%2B-orange?logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-1.3%2B-150458?logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

> Proyek analisis segmentasi pelanggan menggunakan algoritma **K-Means Clustering** untuk mengelompokkan pelanggan berdasarkan karakteristik demografis dan ekonomi, serta menghasilkan **rekomendasi strategi bisnis** per segmen.

---

## 📋 Daftar Isi

- [Gambaran Umum](#-gambaran-umum)
- [Dataset](#-dataset)
- [Metodologi](#-metodologi)
- [Hasil Segmentasi](#-hasil-segmentasi)
- [Visualisasi](#-visualisasi)
- [Insight Bisnis](#-insight-bisnis)
- [Struktur Proyek](#-struktur-proyek)
- [Cara Menjalankan](#-cara-menjalankan)
- [Requirements](#-requirements)

---

## 🔍 Gambaran Umum

Proyek ini bertujuan untuk membantu bisnis memahami **profil pelanggan** secara lebih mendalam melalui pendekatan unsupervised machine learning. Dengan segmentasi yang tepat, perusahaan dapat merancang strategi pemasaran yang lebih terarah dan efisien untuk setiap kelompok pelanggan.

**Highlights:**
- ✅ 1.000 data pelanggan dari berbagai wilayah Indonesia
- ✅ 7 fitur demografis & ekonomi
- ✅ Hierarchical clustering + K-Means clustering
- ✅ Elbow method untuk menentukan jumlah cluster optimal
- ✅ Dashboard visualisasi 4-in-1
- ✅ Radar chart profil segmen
- ✅ Export hasil ke Excel (4 sheet)
- ✅ Rekomendasi strategi bisnis otomatis per segmen

---

## 📂 Dataset

| Kolom | Deskripsi | Tipe |
|---|---|---|
| `jenis_kelamin` | Jenis kelamin pelanggan (LAKI-LAKI / PEREMPUAN) | Kategorikal |
| `status` | Status pernikahan (Menikah / Sendiri) | Kategorikal |
| `umur` | Usia pelanggan (tahun) | Numerik |
| `pendidikan` | Tingkat pendidikan (Lainnya / SMA/SMK / Perguruan Tinggi) | Kategorikal |
| `pendapat` | Pendapatan bulanan (dalam ribuan Rupiah) | Numerik |
| `pekerjaan` | Jenis pekerjaan (Tidak Bekerja / Wiraswasta / Pengusaha) | Kategorikal |
| `kab/kota` | Lokasi domisili pelanggan | Kategorikal |

**Encoding yang diterapkan:**

| Fitur | Encoding |
|---|---|
| Jenis Kelamin | LAKI-LAKI=0, PEREMPUAN=1 |
| Status | Menikah=0, Sendiri=1 |
| Pendidikan | Lainnya=0, SMA/SMK=1, Perguruan Tinggi=2 |
| Pekerjaan | Tidak Bekerja=0, Wiraswasta=1, Pengusaha=2 |
| Wilayah | Kabupaten=0, Kota=1 |

---

## 🔬 Metodologi

```
Raw Data
   │
   ▼
Data Cleaning & Encoding
   │  ├─ Drop kolom tidak relevan (no, penerima, kategori_umur)
   │  ├─ Strip whitespace & perbaiki typo
   │  ├─ LabelEncoder untuk kolom kategorikal
   │  └─ Custom encoding untuk Wilayah
   │
   ▼
Standarisasi (StandardScaler)
   │
   ├──► Hierarchical Clustering → Dendrogram
   │
   ├──► Elbow Method → Menentukan k optimal = 3
   │
   └──► K-Means Clustering (k=3, init='k-means++')
           │
           ▼
      Analisis & Labeling Segmen
           │
           ▼
      Visualisasi & Insight Bisnis
           │
           ▼
      Export Excel
```

---

## 📊 Hasil Segmentasi

Berdasarkan analisis K-Means dengan **k=3**, pelanggan terbagi menjadi 3 segmen:

| Segmen | Jumlah | Proporsi | Rata-rata Umur | Rata-rata Pendapatan |
|---|---|---|---|---|
| 🔵 **Milenial** | 138 orang | 13.8% | 38.2 tahun | Rp 3.585.000 |
| 🟢 **Konsumtif** | 526 orang | 52.6% | 41.6 tahun | Rp 1.803.365 |
| 🔴 **Tidak Konsumtif** | 336 orang | 33.6% | 25.2 tahun | Rp 1.640.304 |

> **Silhouette Score: 0.2461** — menunjukkan cluster yang terbentuk cukup terpisah satu sama lain mengingat data menggunakan campuran fitur demografis multidimensi.

---

## 📈 Visualisasi

Proyek ini menghasilkan **7 visualisasi**:

| No | Visualisasi | Tujuan |
|---|---|---|
| 1 | Dendrogram | Melihat struktur hierarki pengelompokkan | <img width="973" height="726" alt="Image" src="https://github.com/user-attachments/assets/4b787fec-285d-4c4f-bf4f-3d742eb5014e" />
| 2 | Elbow Method | Menentukan jumlah cluster optimal |
| 3 | Heatmap Korelasi | Melihat hubungan antar fitur |
| 4 | Scatter Plot | Distribusi segmen berdasarkan Umur vs Pendapatan |
| 5 | Radar Chart | Profil karakteristik tiap segmen secara holistik |
| 6 | Dashboard 4-in-1 | Bar chart, bar horizontal, box plot umur, stacked bar pekerjaan |
| 7 | Box Plot Pendapatan | Distribusi pendapatan detail per segmen |

---

## 💡 Insight Bisnis

### 🔵 Milenial — *High Income Segment*
> Pendapatan tertinggi (Rp 3.585.000), usia produktif, aktif bekerja

- Tawarkan produk/layanan **premium dan eksklusif**
- Gunakan platform digital (Instagram, TikTok, e-commerce)
- Program **loyalitas & membership** berbasis reward
- Fokus pada kecepatan layanan dan kemudahan transaksi digital

### 🟢 Konsumtif — *Middle Income, Spending Prone*
> Segmen terbesar (52.6%), pendapatan menengah, aktif berbelanja

- Tawarkan **promo, diskon, dan bundling** produk
- Manfaatkan email marketing dan push notification
- Program **cicilan / Buy Now Pay Later (BNPL)**
- Cross-selling dan upselling produk terkait

### 🔴 Tidak Konsumtif — *Budget Conscious Segment*
> Usia muda (rata-rata 25 tahun), pendapatan terendah, cenderung hemat

- Fokus pada produk **harga terjangkau** dan value for money
- Tawarkan program **cashback dan voucher** hemat
- Edukasi finansial sebagai strategi engagement jangka panjang
- Gunakan media sosial organik untuk menjangkau segmen ini

---

## 📁 Struktur Proyek

```
customer-segmentation/
│
├── 📓 customer_segmentation.ipynb  # Jupyter Notebook (dengan %matplotlib inline)
├── 📊 hasil_segmentasi.xlsx        # Output Excel (4 sheet)
├── 📄 cleaned_costumer.csv         # Dataset
└── 📄 README.md                    # Dokumentasi proyek
```

**Sheet dalam `hasil_segmentasi.xlsx`:**

| Sheet | Isi |
|---|---|
| Data Lengkap | 1.000 baris data asli + kolom label segmen |
| Ringkasan Segmen | Rata-rata umur, pendapatan, jumlah & proporsi per segmen |
| Statistik Deskriptif | Min, median, max, std untuk umur & pendapatan per segmen |
| Rekomendasi Bisnis | Profil + strategi bisnis untuk tiap segmen |

---

## 🚀 Cara Menjalankan

**1. Clone repository**
```bash
git clone https://github.com/username/customer-segmentation.git
cd customer-segmentation
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Jalankan via Jupyter Notebook** *(direkomendasikan)*
```bash
jupyter notebook customer_segmentation.ipynb
```

**4. Atau jalankan via Python script**
```bash
python customer_segmentation.py
```

> ⚠️ Pastikan file `cleaned_costumer.csv` berada di direktori yang sama dengan script.

---

## 📦 Requirements

```
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
scikit-learn>=1.0.0
scipy>=1.7.0
openpyxl>=3.0.0
```

Install sekaligus:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy openpyxl
```

---

## 🛠️ Tech Stack

| Library | Kegunaan |
|---|---|
| `pandas` | Manipulasi dan analisis data |
| `numpy` | Komputasi numerik |
| `matplotlib` | Visualisasi dasar |
| `seaborn` | Visualisasi statistik |
| `scikit-learn` | Preprocessing & K-Means clustering |
| `scipy` | Hierarchical clustering & dendrogram |
| `openpyxl` | Export ke Excel dengan formatting |

---

## 👤 Author

**[Agung Zakariah]**
- GitHub: [@agungza](https://github.com/agungza)

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  ⭐ Jika proyek ini bermanfaat, jangan lupa beri <strong>star</strong> di GitHub!
</p>
