# Klasifikasi Jenis Tanaman Berdasarkan Daun

Proyek ini untuk mengklasifikasikan jenis tanaman sehat berdasarkan fitur bentuk, warna, dan tekstur daun menggunakan metode machine learning.

---

## Alur Metode Proyek

Sistem klasifikasi ini dibangun menggunakan 3 tahapan utama:

1. **Segmentasi Citra:** 
   * Menggunakan kombinasi ruang warna **HSV** dan **Otsu Thresholding** untuk memisahkan objek daun secara bersih dari latar belakang (*background*).
2. **Ekstraksi Fitur:**
   * **Fitur Warna:** Ekstraksi komponen warna menggunakan kanal **HSV**.
   * **Fitur Tekstur:** Menggunakan metode **GLCM** (Gray-Level Co-occurrence Matrix).
   * **Fitur Bentuk (Contour):** Mengambil metrik geometris daun berupa *area, perimeter, ratio, extent, solidity,* dan *Hu moments*.
3. **Klasifikasi:**
   * Menggunakan algoritma **Support Vector Machine (Machine Learning)** untuk memprediksi kelas tanaman.

---

## Hasil Performa Model

Pengujian model dilakukan menggunakan total **4.087 data training** dan **1.355 data testing** yang terbagi ke dalam 3 kelas tanaman (*Blueberry, Cherry, Raspberry*).

### 1. Classification Report
* **Akurasi Model (Accuracy):** **97.12%** (`0.9712`)
* Nilai rata-rata *Precision*, *Recall*, dan *F1-Score* di seluruh kelas mencapai **0.97**, menandakan model sangat seimbang dan stabil.

| Kelas Tanaman | Precision | Recall | F1-Score | Jumlah Data (Support) |
| :--- | :---: | :---: | :---: | :---: |
| Blueberry (Healthy) | 0.97 | 0.98 | 0.98 | 454 |
| Cherry (Healthy) | 0.95 | 0.99 | 0.97 | 456 |
| Raspberry (Healthy) | 0.99 | 0.94 | 0.96 | 445 |

### 2. Analisis Confusion Matrix
Berdasarkan visualisasi matriks kontingensi pengujian:
* Kelas **Cherry__healthy** memiliki sensitivitas tertinggi dengan 453 data berhasil diprediksi benar dan hanya 3 data yang salah prediksi.
* Kelas **Raspberry__healthy** memiliki presisi tertinggi (0.99), meskipun ada sedikit misklasifikasi ke arah kelas Blueberry (12 data).

---

## 🔍 Temuan Utama (Findings)

* **Performa Sangat Baik & Stabil:** Kombinasi fitur bentuk (Contour), warna (HSV), dan tekstur (GLCM) terbukti memberikan representasi data yang sangat kaya, sehingga model SVM mampu mengklasifikasikan daun dengan tingkat akurasi tinggi mencapai **97.12%**.
* **Kesalahan Prediksi Minimal:** Melalui evaluasi *Confusion Matrix*, salah prediksi antar kelas daun terjadi dalam jumlah yang sangat sedikit.
* **Kesimpulan:** Metode segmentasi HSV+Otsu yang dipadukan dengan klasifikasi SVM ini terbukti sangat efektif, tangguh, dan akurat untuk diterapkan pada studi kasus identifikasi/klasifikasi jenis tanaman berdasarkan daun.
