# Ringkasan Binary Classification

Pada binary classification, model dilatih untuk memprediksi salah satu dari dua label (contoh: 0 atau 1) berdasarkan fitur-fitur yang tersedia.  
Model seperti logistic regression memanfaatkan fungsi sigmoid (S-shaped) untuk menghitung probabilitas suatu data termasuk ke kelas positif (1) atau negatif (0).  
Beberapa metrik evaluasi utama meliputi:

1. **Accuracy**: Rasio prediksi benar terhadap keseluruhan data uji.  
2. **Recall (True Positive Rate)**: Seberapa baik model menangkap semua kasus positif yang sebenarnya (TP / (TP + FN)).  
3. **Precision**: Persentase prediksi positif yang benar-benar positif (TP / (TP + FP)).  
4. **F1-Score**: Ukuran keseluruhan yang menyeimbangkan recall dan precision (rumus: 2 × (Precision × Recall) ÷ (Precision + Recall)).  
5. **AUC (Area Under the Curve)**: Menggambarkan area di bawah kurva ROC (TPR vs. FPR) pada berbagai nilai threshold. Semakin tinggi AUC (mendekati 1.0), semakin baik model membedakan antara kelas positif dan negatif.

Dengan demikian, sebuah model binary classification yang baik tidak hanya mengedepankan akurasi yang tinggi, tetapi juga memperhatikan keandalan dalam menangkap kasus positif serta akurasi dalam menebak positif secara tepat.
## Contoh Kasus

Misalkan kita memiliki dataset pasien dengan fitur-fitur seperti usia, tekanan darah, kadar kolesterol, dan riwayat kesehatan lainnya. Tujuan kita adalah memprediksi apakah seorang pasien memiliki penyakit jantung (1) atau tidak (0).

1. **Accuracy**: Jika dari 100 pasien, model memprediksi 90 pasien dengan benar (baik positif maupun negatif), maka akurasinya adalah 90%.
2. **Recall**: Dari 50 pasien yang benar-benar memiliki penyakit jantung, jika model berhasil mengidentifikasi 45 di antaranya, recall-nya adalah 90%.
3. **Precision**: Jika model memprediksi 50 pasien memiliki penyakit jantung, dan 45 di antaranya benar-benar memiliki penyakit jantung, precision-nya adalah 90%.
4. **F1-Score**: Menggunakan nilai precision dan recall yang sama (90%), F1-Score-nya adalah 0.90.
5. **AUC**: Jika AUC model adalah 0.95, ini menunjukkan bahwa model sangat baik dalam membedakan antara pasien yang memiliki dan tidak memiliki penyakit jantung.

Dengan contoh ini, kita dapat melihat bagaimana metrik-metrik tersebut digunakan untuk mengevaluasi kinerja model binary classification dalam konteks medis.
