# Bab 1: Pendahuluan

Klasifikasi biner adalah salah satu teknik pembelajaran mesin yang diawasi, mirip dengan regresi. Namun, alih-alih memprediksi nilai numerik, model klasifikasi biner memprediksi salah satu dari dua kelas (misalnya, 0 atau 1). Proses pelatihannya melibatkan beberapa langkah iteratif, yaitu:
1. Melatih model dengan data latih.
2. Memvalidasi model menggunakan subset data yang ditahan.
3. Mengevaluasi performa model untuk memastikan prediksi yang dihasilkan handal.

---

# Bab 2: Dasar Teori Klasifikasi Biner

Model klasifikasi biner dirancang untuk memprediksi satu dari dua kemungkinan label. Contoh klasiknya adalah memprediksi "benar" atau "salah" (1 atau 0). Pada dasarnya, model menghitung probabilitas bahwa suatu pengamatan jatuh ke kelas tertentu:
- P(y=1 | x) menunjukkan probabilitas suatu objek masuk ke kelas 1.
- P(y=0 | x) = 1 – P(y=1 | x).

## Regresi Logistik
Salah satu algoritma populer untuk klasifikasi biner adalah regresi logistik. Meskipun namanya mengandung kata “regresi”, teknik ini digunakan untuk klasifikasi. Algoritma ini memanfaatkan fungsi sigmoid yang berbentuk kurva S, memetakan nilai masukan (x) ke rentang [0,1]. Nilai probabilitas di atas atau sama dengan ambang batas (sering kali 0,5) dikategorikan sebagai 1 (benar), sedangkan di bawah ambang tersebut dikategorikan sebagai 0 (salah).

---

# Bab 3: Contoh Sederhana

Misalkan ingin memprediksi apakah seseorang menderita diabetes hanya berdasarkan satu fitur, yaitu kadar glukosa darah. Berikut contoh data:

| Glukosa Darah (x) | Diabetes? (y) |
| ----------------- | ------------- |
| 67                | 0             |
| 103               | 1             |
| 114               | 1             |
| 72                | 0             |
| 116               | 1             |
| 65                | 0             |

Setelah model dilatih, fungsi sigmoid yang dihasilkan dapat memperkirakan probabilitas y=1 untuk setiap nilai x. Model memprediksi 1 jika probabilitas ≥ 0,5, atau 0 jika sebaliknya.

---

# Bab 4: Pelatihan dan Validasi

Untuk menilai performa model, dibutuhkan data terpisah yang disebut data validasi. Contoh data validasi:

| Glukosa Darah (x) | Diabetes? (y) |
| ----------------- | ------------- |
| 66                | 0             |
| 107               | 1             |
| 112               | 1             |
| 71                | 0             |
| 87                | 1             |
| 89                | 1             |

Model menghasilkan probabilitas untuk setiap titik data. Setelah dibandingkan dengan ambang batas, diperoleh label prediksi. Dengan membandingkan label prediksi (ŷ) dan label asli (y), kebenaran model dapat dihitung melalui berbagai metrik.

---

# Bab 5: Evaluasi Model Klasifikasi Biner

## 1. Matriks Kebingungan (Confusion Matrix)
Matriks kebingungan menampilkan empat kemungkinan hasil:
- True Negative (TN): Prediksi 0, sebenarnya 0.
- False Positive (FP): Prediksi 1, sebenarnya 0.
- False Negative (FN): Prediksi 0, sebenarnya 1.
- True Positive (TP): Prediksi 1, sebenarnya 1.

## 2. Akurasi
Mengukur persentase total prediksi yang benar:
(TP + TN) / (TP + TN + FP + FN).

## 3. Pengenalan (Recall)
Mengukur seberapa banyak kasus positif yang berhasil ditemukan model:
TP / (TP + FN).

## 4. Presisi (Precision)
Mengukur proporsi prediksi positif yang benar-benar positif:
TP / (TP + FP).

## 5. Skor F1
Kombinasi menyeluruh presisi dan pengenalan:
(2 × Presisi × Pengenalan) / (Presisi + Pengenalan).

## 6. Area Under Curve (AUC)
Mengukur kualitas model dengan memplot kurva ROC (Receiver Operating Characteristic). Nilai AUC yang mendekati 1 menandakan model berkinerja sangat baik.

---

# Bab 6: Penutup

Klasifikasi biner menawarkan pendekatan efektif untuk memprediksi dua kelas berbeda. Melalui proses pelatihan, validasi, dan evaluasi, model yang dihasilkan dapat memberikan prediksi andal bagi berbagai kasus, seperti mendeteksi penyakit atau memfilter email spam. Pemahaman konsep, algoritma, dan metrik evaluasi yang tepat sangat penting guna memastikan kualitas prediksi yang dihasilkan.
