# Cross-Soft Clustering & Classification untuk UMKM Indonesia

## 📌 Deskripsi Proyek

Proyek ini mengimplementasikan **Cross-Soft Clustering** yang dikombinasikan dengan **model klasifikasi machine learning** untuk menganalisis dan memprediksi kinerja keuangan **Usaha Mikro, Kecil, dan Menengah (UMKM)** di Indonesia.

Pendekatan yang digunakan tidak hanya melakukan segmentasi (clustering), tetapi juga **mengintegrasikan hasil klaster ke dalam pemodelan prediktif**, sehingga menghasilkan analisis yang lebih komprehensif dan presisi.

Studi kasus utama adalah **klasifikasi status laba UMKM (untung/rugi)** berdasarkan karakteristik usaha dan kinerja keuangan.

---

## 🎯 Tujuan Penelitian

1. Melakukan **Exploratory Data Analysis (EDA)** untuk memahami karakteristik UMKM.
2. Melakukan **clustering dengan pendekatan cross-cluster** berdasarkan dua kategori utama:

   * Struktur & Profil Usaha
   * Kinerja & Skala Usaha
3. Membangun **model klasifikasi status laba UMKM** menggunakan algoritma ensemble machine learning berbasis hasil cross-cluster.

---

## 🧠 Konsep Utama: Cross-Soft Clustering

Cross-soft clustering dilakukan dengan cara:

1. Membagi fitur ke dalam **dua kelompok karakteristik usaha**.
2. Melakukan **soft clustering** secara terpisah pada masing-masing kelompok fitur.
3. Menggabungkan hasil klaster dari kedua kelompok untuk membentuk **cross-cluster**.
4. Melakukan **pemodelan klasifikasi terpisah pada setiap cross-cluster**.

Pendekatan ini memungkinkan model menangkap **heterogenitas struktural dan performa usaha** secara lebih baik dibandingkan clustering tunggal.

---

## 📊 Dataset & Fitur

### Kategori Struktur & Profil Usaha

* jenis_usaha (kategorik)
* tenaga_kerja_perempuan
* tenaga_kerja_laki_laki
* kapasitas_produksi
* tahun_berdiri
* marketplace
* status_legalitas

### Kategori Kinerja & Skala Usaha

* aset
* omset
* biaya_karyawan
* jumlah_pelanggan

### Target Variabel

* **klas_laba** (hasil feature engineering):

  * `Untung` jika laba > 0
  * `Rugi` jika laba ≤ 0

---

## ⚙️ Metodologi

### 1. Pra-pemrosesan Data

* Identifikasi missing value
* Imputasi menggunakan **K-NN Imputer**
* Label Encoding untuk variabel kategorik
* Standardisasi fitur numerik
* Pengecekan multikolinieritas (VIF)

### 2. Clustering

Algoritma yang dievaluasi:

* K-Prototypes
* K-Medoids (Gower Distance)
* Agglomerative Clustering (Gower)
* **Adaptive K-Means** ✅ (terbaik)

Evaluasi clustering menggunakan:

* Silhouette Score
* Davies–Bouldin Index
* Calinski–Harabasz Index

Jumlah klaster optimum: **2 klaster** untuk masing-masing kategori.

### 3. Cross-Cluster

Hasil penggabungan klaster menghasilkan **4 cross-cluster**:

* Cluster 00
* Cluster 01
* Cluster 10
* Cluster 11

---

## 🤖 Pemodelan Klasifikasi

Algoritma yang digunakan:

* XGBoost
* CatBoost
* LightGBM
* Random Forest

### Optimasi Hyperparameter

* Menggunakan **Optuna**
* Jumlah trial: 50

### Evaluasi Model

* AUC
* Balanced Accuracy

### Model Terbaik per Cross-Cluster

| Cross-Cluster | Model Terbaik |
| ------------- | ------------- |
| Cluster 00    | LightGBM      |
| Cluster 01    | CatBoost      |
| Cluster 10    | CatBoost      |
| Cluster 11    | CatBoost      |

---

## 🔍 Insight Utama

* **Variabel aset** secara konsisten menjadi faktor paling berpengaruh di seluruh cross-cluster.
* Pendekatan cross-cluster meningkatkan stabilitas dan interpretabilitas model.
* Model CatBoost unggul pada data dengan kombinasi fitur numerik dan kategorik.

---

## 📌 Kontribusi & Manfaat

* **Pelaku UMKM**: memahami posisi usaha dan faktor penentu kinerja
* **Pemerintah**: perumusan kebijakan berbasis data
* **Akademisi**: pendekatan metodologis baru dalam integrasi clustering–classification

---

## 👥 Tim

**StatStorm – Politeknik Statistika STIS**

* Suhendra Widi Prayoga
* Muh Farhan
* Dutatama Rosewika Taufiq Hadihardaya

---

## 📜 Lisensi

Proyek ini digunakan untuk keperluan **Data Mining in Information System Competition DISCO UTM 2025**.

---

> *“Data science bukan hanya tentang membangun model, tetapi membangun solusi.”*