# Deep Learning

Deep learning adalah cabang dari machine learning yang dirancang untuk meniru cara kerja otak manusia dalam memproses informasi. Metode ini menggunakan serangkaian lapisan neuron buatan (*artificial neural networks* atau *ANNs*) yang saling terhubung. Setiap neuron buatan bertindak seperti fungsi matematika yang:
- Menerima input
- Mengalikannya dengan bobot (*weight*)
- Menambahkan bias (bila ada)
- Memproses hasilnya melalui fungsi aktivasi

## Mengapa Disebut "Deep" Learning?

Deep learning melibatkan banyak lapisan neuron:
1. Data masuk melalui lapisan paling awal (*input layer*)
2. Diolah melalui beberapa lapisan tersembunyi (*hidden layers*)
3. Lapisan paling akhir (*output layer*) memberikan hasil akhir

Karena terdapat banyak lapisan yang berurutan, fungsinya menjadi "dalam" (*deep*). Itulah mengapa metode ini dinamakan deep learning.

## Struktur Jaringan Syaraf Buatan (Artificial Neural Network)

### Input Layer
- Menampung data atau fitur yang akan diproses
- Contoh: panjang paruh, lebar paruh, panjang sirip, dan berat penguin

### Hidden Layers
- Kumpulan neuron yang mengolah dan mempelajari pola-pola hubungan antar fitur
- Setiap neuron menghitung nilai dari input yang masuk dengan bobot (*weight*) tertentu
- Meneruskan hasilnya jika memenuhi syarat aktivasi

### Output Layer
- Menyimpulkan hasil akhir
- Contoh: untuk klasifikasi penguin, output layer akan menyajikan prediksi probabilitas penguin tersebut termasuk spesies:
  - Adelie
  - Gentoo
  - Chinstrap

## Cara Kerja dan Proses Pelatihan (Training)

### 1. Forward Pass (Maju ke Depan)
- Data (x) dimasukkan ke input layer
- Nilai x dihitung oleh tiap neuron dengan bobot-bobot (*weight*) yang berlaku
- Hasil diteruskan ke lapisan berikutnya hingga mencapai output layer
- Output layer menghasilkan perkiraan (prediksi) untuk label tertentu

### 2. Fungsi Loss (Kerugian)
- Prediksi (ŷ) dibandingkan dengan label sebenarnya (y)
  - Contoh: jika label sebenarnya adalah "Chinstrap" ([0, 0, 1]), tetapi model memprediksi [0.3, 0.1, 0.6]
- Selisih diringkas ke dalam satu nilai "loss" yang mewakili seberapa buruk kinerja model

### 3. Backpropagation (Balik Mundur) dan Gradient Descent
- Model mengukur efek setiap bobot terhadap hasil loss
- Mengubah bobot untuk meminimalkan loss menggunakan gradient descent
- Perubahan bobot menyebar mundur dari output layer ke lapisan-lapisan sebelumnya
- Proses ini diulang berkali-kali (setiap pengulangan disebut "epoch")

## Contoh dalam Klasifikasi Penguin

### Fitur Input
1. Panjang paruh
2. Kedalaman paruh
3. Panjang sirip
4. Berat penguin

### Proses Klasifikasi
- Model melakukan klasifikasi multi-kelas (Adelie, Gentoo, atau Chinstrap)
- Setiap neuron di input layer mewakili satu fitur penguin
- Fitur-fitur dikombinasikan dan dihitung melalui bobot yang disesuaikan
- Output layer menghasilkan tiga nilai probabilitas
  - Contoh: [0.2, 0.7, 0.1]
  - Nilai tertinggi (0.7) menunjukkan prediksi spesies Gentoo

## Kesimpulan

Deep learning sangat berguna untuk masalah yang kompleks, seperti:
- Pengenalan gambar
- Pemrosesan bahasa alami
- Dan aplikasi kompleks lainnya

### Keunggulan
- Mampu mengekstraksi sendiri ciri-ciri penting dari data
- Tidak memerlukan pembuatan fitur secara manual (*feature engineering*)

### Keterbatasan
- Memerlukan banyak data
- Membutuhkan daya komputasi yang besar
- Kebutuhan resources meningkat seiring jumlah lapisan dan neuron