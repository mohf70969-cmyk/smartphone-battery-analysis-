# Prediksi Konsumsi Baterai Smartphone Berdasarkan Pola Aktivitas Digital Pengguna

## Deskripsi Proyek

Proyek ini bertujuan memprediksi tingkat kesehatan baterai smartphone (`current_battery_health_percent`) berdasarkan pola aktivitas digital pengguna menggunakan tiga model regresi: **Linear Regression**, **Ridge Regression**, dan **Random Forest**.

Analisis dilakukan dalam framework Jupyter Notebook sebagai bagian dari tugas Statistika & Probabilitas.

---

## Dataset

| File | Keterangan | Baris | Kolom |
|---|---|---|---|
| `smartphone_battery_features.csv` | Fitur pola aktivitas digital | 5.000 | 15 |
| `smartphone_battery_targets.csv` | Target: battery health % | 5.000 | 3 |

**Sumber:** Kaggle — Smartphone Battery Degradation Dataset  
**Lisensi:** CC0 Public Domain

### Fitur Utama
- `device_age_months` — Usia perangkat (bulan)
- `avg_screen_on_hours_per_day` — Rata-rata screen on time (jam/hari)
- `avg_charging_cycles_per_week` — Frekuensi pengisian per minggu
- `avg_battery_temp_celsius` — Suhu baterai rata-rata (°C)
- `gaming_hours_per_week` — Jam gaming per minggu
- `video_streaming_hours_per_week` — Jam streaming per minggu
- `charging_habit_score` — Skor kebiasaan pengisian
- `thermal_stress_index` — Indeks stres termal

**Target:** `current_battery_health_percent` — Persentase kesehatan baterai saat ini

---

## Metode

| Model | Keterangan |
|---|---|
| Linear Regression | Baseline: hubungan linier fitur–target |
| Ridge Regression | Linear dengan regularisasi L2 |
| Random Forest | Ensemble 150 decision trees |

---

## Hasil Evaluasi

| Model | R² | MAE | RMSE |
|---|---|---|---|
| Linear Regression | 0.9298 | 3.6777% | 4.6872% |
| Ridge Regression | 0.9298 | 3.6810% | 4.6869% |
| **Random Forest** | **0.9580** | **2.9159%** | **3.6265%** |

**Random Forest** adalah model terbaik dengan R² = **0.9580**.

---

## Struktur File

```
.
├── analysis.ipynb              ← Notebook utama (semua kode & output)
├── smartphone_battery_features.csv
├── smartphone_battery_targets.csv
├── README.md                   ← File ini
├── requirements.txt            ← Daftar library Python
├── CARA_PENGGUNAAN.txt         ← Panduan menjalankan project
└── grafik/
    ├── 01_distribusi_target.png
    ├── 02_heatmap_korelasi.png
    ├── 03_scatter_fitur_target.png
    ├── 04_distribusi_aktivitas.png
    ├── 05_battery_per_kategori.png
    ├── 06_perbandingan_model.png
    ├── 07_actual_vs_predicted.png
    └── 08_feature_importance.png
```

---

## Temuan Utama

1. **Usia perangkat** adalah prediktor terkuat (r = −0.854).
2. **Screen on time** dan **siklus pengisian** berkorelasi negatif signifikan.
3. **Kebiasaan pengisian yang baik** memperlambat degradasi baterai.
4. **Suhu tinggi** mempercepat penurunan kapasitas.

---

## Rekomendasi Praktis

- Batasi screen on time < 6 jam/hari
- Hindari pengisian semalam (overnight charging) setiap hari
- Jaga suhu perangkat, terutama saat gaming atau streaming
- Isi daya di rentang 20–80% untuk memperpanjang umur baterai
