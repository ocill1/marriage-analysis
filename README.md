# 💍 Prediksi Jumlah Pernikahan per Provinsi di Indonesia

Beberapa waktu lalu gua mulai notice sesuatu — iklan KUA mulai muncul di mana-mana. Di Instagram, TikTok, bahkan YouTube. Dan ternyata bukan tanpa alasan: angka pernikahan di Indonesia turun tiap tahun, dari **2 juta lebih di 2018 jadi di bawah 1,5 juta di 2024**. Penurunan hampir 27% dalam 6 tahun.

Proyek ini adalah usaha gua buat memahami: **faktor apa yang paling berpengaruh terhadap jumlah pernikahan di suatu provinsi?** Dan bisakah kita memprediksinya?

---

## 🔍 Temuan Menarik

Ada 4 provinsi yang bikin gua penasaran — IPM-nya tinggi, kemiskinannya rendah, tapi jumlah pernikahannya justru di bawah rata-rata nasional:

| Provinsi | Jumlah Nikah (2024) | IPM | Kemiskinan (%) |
|----------|-------------------|-----|----------------|
| Bali | 3.189 | 77,76 | 4,00 |
| Sulawesi Utara | 6.025 | 75,03 | 7,25 |
| Kep. Bangka Belitung | 7.973 | 73,33 | 4,55 |
| Kepulauan Riau | 11.533 | 77,97 | 5,37 |

Provinsi-provinsi ini sejahtera secara ekonomi, tapi justru angka pernikahannya rendah. Ini menunjukkan bahwa **kemapanan ekonomi tidak selalu berbanding lurus dengan keinginan menikah** — ada faktor lain seperti gaya hidup, urbanisasi, dan pergeseran nilai sosial yang mungkin berperan.

---

## 📉 Tren Nasional

```
2018 → 2.016.171
2019 → 1.968.978
2020 → 1.780.346  ← pandemi mulai
2021 → 1.742.049
2022 → 1.705.348
2023 → 1.574.326
2024 → 1.478.302
```

Penurunan paling drastis terjadi di 2020 (pandemi), tapi yang mengkhawatirkan adalah penurunan **terus berlanjut bahkan setelah pandemi berakhir**.

---

## 🤖 Pendekatan

Proyek ini menggunakan **Supervised Machine Learning (Regression)** untuk memprediksi jumlah pernikahan per provinsi berdasarkan 3 fitur:

- Indeks Pembangunan Manusia (IPM)
- Tingkat Pengangguran Terbuka (TPT)
- Persentase Penduduk Miskin

Dua model dibandingkan: **Linear Regression** vs **Random Forest Regressor**.

---

## 📊 Hasil

| Model | R² Score | RMSE |
|-------|----------|------|
| Linear Regression | ~0.65 | ~lebih tinggi |
| **Random Forest** | **0.7561** ✅ | lebih rendah |

**Random Forest menang** — artinya hubungan antara kemiskinan, IPM, pengangguran, dan jumlah pernikahan tidak bersifat linear. Ada interaksi kompleks antar variabel yang hanya bisa ditangkap model non-linear.

**Fitur paling berpengaruh: Kemiskinan**

Ini yang paling mengejutkan — ternyata kemiskinan punya pengaruh lebih besar dari IPM maupun pengangguran terhadap jumlah pernikahan. Provinsi dengan kemiskinan tinggi cenderung punya jumlah pernikahan yang lebih bervariasi dan susah diprediksi.

---

## 🗂️ Struktur Proyek

```
marriage-analysis/
│
├── data/
│   ├── Nikah dan Cerai Menurut Provinsi, 2018-2024.csv
│   ├── bps-od_15042_indeks_pmbngnn_manusia.csv
│   ├── bps-od_20206_tingkat_pengangguran_terbuka.csv
│   ├── bps-od_20948_persentase_penduduk_miskin.csv
│   └── dataset_gabungan.csv
│
├── models/
│   ├── rf_model.pkl
│   └── scaler.pkl
│
├── notebooks/
│   └── marriage_analysis.ipynb
│
└── README.md
```

---

## ⚙️ Cara Menjalankan

```bash
git clone https://github.com/ocill1/marriage-analysis.git
cd marriage-analysis
pip install pandas numpy matplotlib seaborn scikit-learn joblib
jupyter notebook notebooks/marriage_analysis.ipynb
```

---

## 📚 Sumber Data

- [BPS — Nikah dan Cerai Menurut Provinsi](https://www.bps.go.id)
- [Open Data Jabar — IPM per Provinsi](https://opendata.jabarprov.go.id)
- [Open Data Jabar — Tingkat Pengangguran](https://opendata.jabarprov.go.id)
- [Open Data Jabar — Persentase Penduduk Miskin](https://opendata.jabarprov.go.id)

---

## 👤 Author

**Mochmad Ilham Nadhif**  
Teknik Informatika — Universitas Dian Nuswantoro  
`A11.2024.15995`
