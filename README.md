# 🚗 Prediksi Harga Mobil Bekas di Arab Saudi

> ⚠️ **Disclaimer**  
> Dalam pembuatan grafik pada proyek ini, tim menggunakan **library Plotly** untuk menghasilkan visualisasi yang lebih **interaktif**. Namun, perlu diketahui bahwa grafik berbasis Plotly **tidak dapat ditampilkan secara langsung di halaman GitHub**.  
> Untuk melihat grafik interaktif tersebut, Anda perlu membuka file notebook menggunakan environment yang mendukung rendering Plotly seperti **Visual Studio Code**.

---

## 📌 Ringkasan Proyek

Proyek ini bertujuan untuk membangun model prediksi harga mobil bekas di Arab Saudi berdasarkan fitur kendaraan seperti merek, tahun, kilometer, ukuran mesin, jenis transmisi, dan lainnya. Model dilatih menggunakan dataset dari syarah.com dan di-deploy melalui Streamlit untuk interaksi publik.

---

## 📊 Eksplorasi dan Pembersihan Data

- Menghapus 2.526 baris dengan `Price = 0`
- Menghapus kolom tidak relevan: `Negotiable`, `Region`
- Menangani outlier menggunakan pengetahuan domain dan metode IQR
- Standardisasi fitur kategorikal dan numerik menggunakan `TargetEncoder`, `OrdinalEncoder`, dan `StandardScaler`

---

## 🧠 Pendekatan Modeling

Model regresi yang digunakan:

- Linear Regression, Ridge, Lasso, ElasticNet
- KNN Regressor, Decision Tree Regressor
- Random Forest Regressor
- Gradient Boosting Regressor
- Support Vector Regressor
- XGBoost Regressor

**Metrik Evaluasi**:
- RMSE, MAE, MAPE, R² Score

---

## 🏆 Model Terbaik

| Model               | MAPE (%) |
|---------------------|----------|
| Tuned XGBoost       | **11.95** |
| Tuned Random Forest | 12.44    |

---

## 🔧 Hyperparameter Tuning (Optuna)

- Menggunakan 50 trials dengan RepeatedKFold
- Objective: Minimisasi MAPE
- Parameter XGBoost yang dituning: `n_estimators`, `max_depth`, `learning_rate`, `subsample`, `colsample_bytree`, `gamma`, `reg_alpha`, `reg_lambda`, `min_child_weight`

---

## 🗂️ Struktur File

```
📦 Saudi-Used-Cars-Price-Prediction
├── Final Project.py        # File proyek dalam bentuk script
├── README.md                  # Dokumentasi proyek
├── best_xgb_model.pkl         # Model final XGBoost
├── target_encoder.pkl         # Encoder untuk 'Type', 'Color', 'Make'
├── ordinal_encoder.pkl        # Encoder untuk 'Fuel_Type', 'Gear_Type', dll
├── scaler.pkl                 # Scaler untuk fitur numerik
```

---

## 🌐 Demo Aplikasi

- **Streamlit App** (uji prediksi harga):  
  👉 https://saudi-arabia-used-cars-price-prediction.streamlit.app/

- **Dashboard Tableau (Visualisasi EDA)**:  
  👉 https://public.tableau.com/app/profile/evelio.excellenta/viz/MobilBekasArabSaudiAnalysis/Story2

---

## 👥 Kontributor

- **Muhammad Daffa Hilmy**
- **Evelio Excellenta**

---

## 📌 Dampak Bisnis

Model ini dapat digunakan untuk:
- Memprediksi harga wajar mobil bekas
- Mengurangi ketidakpastian harga dan waktu negosiasi
- Meningkatkan kepercayaan pengguna pada platform digital
- Membantu lembaga keuangan dalam penilaian dan keputusan pembiayaan

---

## 📈 Pengembangan Selanjutnya

- **Perluasan Dataset:** Integrasikan data tambahan seperti kondisi kendaraan, riwayat servis, dan ulasan pasar untuk meningkatkan cakupan dan representativitas.
- **Update Berkala:** Lakukan retraining dan validasi model secara periodik untuk memastikan model tetap akurat seiring dengan perubahan tren pasar.
- **Integrasi Umpan Balik:** Kembangkan mekanisme feedback loop dari transaksi nyata untuk terus mengkalibrasi dan meningkatkan performa model.
- **Eksplorasi Metode Lanjutan:** Pertimbangkan penggunaan metode hybrid atau deep learning untuk menangani kompleksitas dan non-linearitas yang mungkin tidak tertangkap oleh model saat ini.
- **Penambahan Fitur Kontekstual:** Tambahkan fitur-fitur yang lebih kontekstual seperti indikator ekonomi, lokasi penjualan, atau tren musiman untuk meningkatkan prediktabilitas.
