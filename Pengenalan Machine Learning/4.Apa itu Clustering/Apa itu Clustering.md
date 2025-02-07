# Clustering dalam Machine Learning

Clustering adalah metode *unsupervised learning* dalam machine learning yang bertujuan mengelompokkan data ke dalam beberapa kelompok (cluster) berdasarkan kesamaan fitur. Proses ini tidak menggunakan label atau kategori yang telah ditetapkan sebelumnya, melainkan hanya mengandalkan pola internal yang ditemukan di dalam data.

## 1. Pengertian Clustering

- **Definisi Singkat:**  
  Clustering mengelompokkan data yang memiliki karakteristik atau fitur serupa ke dalam satu cluster. Dengan demikian, data dalam cluster yang sama seharusnya sangat mirip, sementara data di cluster berbeda seharusnya memiliki perbedaan.

- **Contoh Umum:**  
  Seorang botanis mencatat dua fitur bunga: jumlah daun (x1) dan jumlah kelopak (x2). Meskipun tidak ada label jenis bunga, kita dapat membagi bunga-bunga tersebut menjadi beberapa kelompok berdasarkan kemiripannya di ruang dua dimensi.

## 2. Algoritma K-Means

### 2.1 Konsep Utama

K-Means adalah algoritma populer untuk clustering. Tujuannya adalah menemukan posisi centroid yang optimal untuk setiap cluster. Berikut tahapan utamanya:

1. **Tentukan jumlah cluster (k):**  
   Misalnya, k = 3 berarti data akan dibagi menjadi tiga kelompok.

2. **Inisialisasi centroid:**  
   Pilih k titik secara acak di ruang fitur sebagai centroid awal.

3. **Penugasan (Assignment):**  
   Hitung jarak antara setiap data dan setiap centroid. Masukkan data ke cluster yang centroid-nya paling dekat.

4. **Perbarui centroid:**  
   Setelah penugasan, pindahkan centroid ke posisi baru dengan menghitung rata-rata (mean) posisi data pada tiap cluster.

5. **Iterasi:**  
   Ulangi proses penugasan dan perbaruan centroid sampai posisi centroid stabil atau tercapai batas iterasi tertentu.

### 2.2 Ilustrasi Singkat
Misalkan kita memiliki data sebagai berikut:

| Leaves (x1) | Petals (x2) |
|-------------|-------------|
| 0           | 5           |
| 0           | 6           |
| 1           | 3           |
| 1           | 3           |
| 1           | 6           |
| 1           | 8           |
| 2           | 3           |
| 2           | 7           |
| 2           | 8           |

1. Tentukan k, misalnya k = 3.  
2. Pilih tiga titik acak sebagai centroid awal.  
3. Tentukan jarak setiap bunga ke centroid dan masukkan bunga ke centroid terdekat.  
4. Pindahkan centroid sesuai rata-rata posisi bunga di dalam tiap cluster.  
5. Ulangi hingga posisi centroid tidak berubah signifikan.

## 3. Evaluasi Hasil Clustering

Karena tidak ada label, penilaian kualitas cluster bertumpu pada seberapa baik cluster memisahkan data. Beberapa metrik yang sering digunakan:

- **Jarak Rata-Rata ke Centroid (Within-Cluster):**  
  Mengukur rata-rata jarak data dalam cluster ke centroid. Makin kecil, makin kompak.

- **Jarak Antar Centroid (Between-Cluster):**  
  Mengukur jarak rata-rata antar centroid. Semakin besar jarak, semakin terpisah cluster.

- **Jarak Maksimum ke Centroid:**  
  Mengukur jarak terjauh data dalam satu cluster terhadap centroid-nya. Dapat mendeteksi adanya outlier.

- **Silhouette Score:**  
  Menghasilkan nilai antara -1 hingga 1 yang mencerminkan seberapa baik data dikelompokkan. Mendekati 1 artinya baik, sementara mendekati -1 menandakan kemungkinan data tergolong ke cluster yang keliru.

## 4. Aplikasi Clustering

- **Segmentasi Pasar:**  
  Pembagian pelanggan berdasarkan kemiripan perilaku atau demografi.

- **Analisis Gambar:**  
  Melacak pola serupa dalam gambar, misalnya pengelompokan objek berdasarkan fitur visualnya.

- **Riset Ilmiah:**  
  Mengelompokkan data eksperimen atau sampel biologis untuk menemukan hubungan tersembunyi yang belum diketahui.

## 5. Studi Kasus Sederhana

Data bunga yang hanya memiliki dua fitur, jumlah daun dan jumlah kelopak, dapat dibagi menjadi beberapa cluster menggunakan K-Means. Meskipun tanpa label spesies bunga, kita tetap dapat menemukan pola pengelompokan yang bermanfaat dalam analisis.

## 6. Kesimpulan

Clustering memberikan cara ampuh untuk menemukan pola tersembunyi pada dataset tanpa memerlukan label. K-Means menjadi salah satu algoritma paling populer untuk tugas ini, meski masih banyak algoritma lain (misalnya DBSCAN, Hierarchical Clustering) yang dapat digunakan sesuai kebutuhan. Dengan memahami tahapan dan konsep dasarnya, kita dapat memanfaatkan teknik clustering di berbagai bidang, dari bisnis hingga penelitian.