# Klasifikasi Multikelas

## Materi 1: Pengertian Klasifikasi Multikelas
Klasifikasi multikelas adalah teknik machine learning untuk memprediksi kelas dari suatu observasi di antara beberapa kemungkinan kelas. Ini adalah metode supervised learning, artinya model dilatih menggunakan data yang sudah memiliki label. Prosesnya melibatkan:
- **Pelatihan model**
- **Validasi dengan data yang dipisahkan**
- **Evaluasi performa**

### Contoh Kasus
**Data:** Pengamatan spesies penguin berdasarkan panjang sirip (fitur *x*).  
**Label Kelas (y):**
- 0: Adelie
- 1: Gentoo
- 2: Chinstrap

**Tabel Data Contoh:**

| Panjang Sirip (x) | Spesies (y) |
|-------------------|-------------|
| 167               | 0           |
| 172               | 0           |
| 225               | 2           |
| 197               | 1           |

## Materi 2: Algoritma untuk Klasifikasi Multikelas
Ada dua pendekatan utama:

### 1. One-vs-Rest (OvR)
#### Cara Kerja:
- Membuat satu model biner untuk setiap kelas.
- Setiap model memprediksi apakah observasi termasuk ke dalam kelas target atau bukan.

#### Contoh untuk Kasus Penguin:
- **Model 1:** Adelie vs Bukan Adelie
- **Model 2:** Gentoo vs Bukan Gentoo
- **Model 3:** Chinstrap vs Bukan Chinstrap

**Prediksi:**  
Hasil akhir adalah kelas dengan probabilitas tertinggi dari semua model.

### 2. Algoritma Multinomial
#### Cara Kerja:
- Membuat satu model tunggal yang menghitung distribusi probabilitas semua kelas.
- Menggunakan fungsi seperti **softmax** untuk menghasilkan vektor probabilitas.

#### Contoh Output:
[0.2, 0.3, 0.5] → Prediksi kelas 2 (Chinstrap)

**Perbedaan dengan OvR:**
- **OvR:** Terpisah, model independen untuk tiap kelas.
- **Multinomial:** Satu model yang menghitung semua kelas sekaligus.

## Materi 3: Evaluasi Model Klasifikasi Multikelas
Evaluasi dilakukan menggunakan:
- **Matriks Kebingungan (Confusion Matrix)**
- **Metrik:** akurasi, recall, precision, dan F1-score

### Contoh Hasil Validasi:
| Panjang Sirip (x) | Spesies Aktual (y) | Spesies Prediksi (ŷ) |
|-------------------|--------------------|----------------------|
| 165               | 0                  | 0                    |
| 205               | 2                  | 1                    |
| 221               | 2                  | 2                    |

**Matriks Kebingungan:**

|               | Prediksi 0 | Prediksi 1 | Prediksi 2 |
|---------------|------------|------------|------------|
| **Aktual 0**  | 2          | 0          | 0          |
| **Aktual 1**  | 0          | 2          | 0          |
| **Aktual 2**  | 0          | 1          | 2          |

### Metrik per Kelas (Contoh untuk Kelas 0):
- **TP (True Positive):** 2  
- **TN (True Negative):** 5  
- **FP (False Positive):** 0  
- **FN (False Negative):** 0  

#### Perhitungan:
- **Akurasi:** (TP + TN) / Total = (2 + 5) / 7 = 1.0  
- **Recall:** TP / (TP + FN) = 2 / 2 = 1.0  
- **Precision:** TP / (TP + FP) = 2 / 2 = 1.0  

### Metrik Agregat (Overall):
- **Akurasi:** (Total Prediksi Benar) / (Total Data) = (2+2+2) / 7 ≈ 0.86  
- **Recall:** Rata-rata recall tiap kelas = (1.0 + 1.0 + 0.67) / 3 ≈ 0.89  
- **Precision:** Rata-rata precision tiap kelas = (1.0 + 0.67 + 1.0) / 3 ≈ 0.89  
- **F1-Score:** Rata-rata harmonik recall dan precision ≈ 0.89  

## Materi 4: Contoh Perhitungan Metrik
#### Rumus:
- **Akurasi:** (TP + TN) / (TP + TN + FP + FN)
- **Recall:** TP / (TP + FN)
- **Precision:** TP / (TP + FP)
- **F1-Score:** 2 × (Precision × Recall) / (Precision + Recall)

#### Aplikasi pada Data (Contoh untuk Kelas 2):
- **TP:** 2 (prediksi benar kelas 2)
- **FP:** 0 (observasi bukan kelas 2 tapi diprediksi 2)
- **FN:** 1 (observasi kelas 2 tapi diprediksi 1)

**Perhitungan:**
- **Recall:** 2 / (2 + 1) = 0.67  
- **Precision:** 2 / (2 + 0) = 1.0  

## Ringkasan
- Klasifikasi multikelas memungkinkan prediksi ke lebih dari dua kelas.
- Algoritma **OvR** dan **Multinomial** adalah pendekatan umum.
- Evaluasi dilakukan menggunakan matriks kebingungan dan metrik seperti akurasi, recall, precision, dan F1-score.
- Metrik dapat dihitung per kelas atau secara agregat.