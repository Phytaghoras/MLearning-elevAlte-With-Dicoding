# Modul Pembelajaran: Menguasai GitHub Copilot dengan Rekayasa Prompt

## Bagian 1: Pengenalan GitHub Copilot dan Rekayasa Prompt
**Narasi Pembuka: Revolusi AI dalam Pengembangan Perangkat Lunak**  
Bayangkan Anda memiliki asisten pengkodean yang memahami jutaan baris kode dan pola pemrograman. GitHub Copilot, didukung oleh OpenAI, adalah mitra AI yang membantu Anda menulis kode lebih cepat dan efisien. Namun, seperti mengajari rekan kerja baru, kunci keberhasilannya terletak pada cara Anda berkomunikasi. Di sinilah rekayasa prompt berperan—seni merancang instruksi yang jelas untuk menghasilkan kode yang presisi.

## Bagian 2: Fondasi Rekayasa Prompt
### Prinsip 4S: Panduan Dasar untuk Instruksi yang Efektif
1. **Tunggal (Single)**  
    - Contoh Analogi: Seperti memesan kopi di kedai. Anda tidak mengatakan, "Buatkan saya minuman," tetapi, "Saya ingin espresso dengan tambahan susu oat."  
    - Praktik: Fokus pada satu tugas per prompt.  
    - Contoh Buruk: "Buat fungsi untuk menghitung dan menampilkan data."  
    - Contoh Baik: "Buat fungsi Python untuk menghitung rata-rata dari list angka dan kembalikan hasilnya dengan dua desimal."

2. **Spesifik (Specific)**  
    - Analogi: Seperti memberi koordinat GPS alih-alih petunjuk arah kabur.  
    - Praktik: Sertakan detail teknis (bahasa, framework, parameter).

```python
# Buruk: "Buat fungsi untuk menghitung diskon."
# Baik: "Buat fungsi Python bernama hitung_diskon yang menerima total_belanja (float) dan status_member (bool). 
# Jika status_member=True, berikan diskon 15%, else 5%."
```

3. **Pendek (Short)**  
    - Keseimbangan: Jelas tanpa bertele-tele. Hindari kalimat panjang yang membingungkan.  
    - Contoh:  
      - Buruk: "Buat kode untuk sistem login yang aman, termasuk validasi password, hash, dan session management, mungkin menggunakan Flask dengan database SQL..."  
      - Baik: "Buat fungsi login dengan Flask yang memvalidasi password (minimal 8 karakter, 1 angka), menyimpan hash di SQLite, dan mengelola session dengan JWT."

4. **Kelilingi (Surround)**  
    - Analogi: Memberikan peta lengkap saat meminta jalan.  
    - Praktik: Buka file terkait dan gunakan komentar untuk konteks.

```python
# File: authentication.py
# Konteks: Sistem ini menggunakan Flask-SQLAlchemy. 
# Fungsi ini harus memeriksa email unik sebelum registrasi.
def check_email_unik(email):
     # Biarkan Copilot melanjutkan...
```

## Bagian 3: Praktik Terbaik Rekayasa Prompt Lanjutan
1. **Sertakan Contoh untuk Pembelajaran Terarah**  
    - Pembelajaran Tanpa Contoh (Zero-Shot):

```python
# Prompt: "Buat fungsi untuk mengonversi suhu dari Celcius ke Fahrenheit."
# Output Copilot:
def celcius_ke_fahrenheit(c):
     return (c * 9/5) + 32
```

    - Pembelajaran dengan Contoh (One-Shot/Multi-Shot):

```python
# Contoh One-Shot:
# Fungsi konversi km ke mil: 1 km = 0.621371 mil
def km_ke_mil(km):
     return km * 0.621371

# Prompt: "Buat fungsi serupa untuk mengonversi kilogram ke pound (1 kg = 2.20462 lb)."
# Output Copilot:
def kg_ke_pound(kg):
     return kg * 2.20462
```

2. **Iterasi untuk Hasil Optimal**  
    - Contoh Iterasi:  
      - Prompt Awal: "Buat kode untuk sorting list angka."  
         Output mungkin menggunakan bubble sort yang kurang efisien.  
      - Prompt Diperbaiki: "Buat fungsi sorting di Python menggunakan algoritma quicksort dengan parameter list angka dan kembalikan list terurut ascending."  
         Output akan lebih presisi dan efisien.

3. **Manfaatkan Konteks Proyek**  
    - Tips:  
      - Buka file config.py atau models.py di IDE agar Copilot memahami struktur proyek.  
      - Gunakan komentar di atas fungsi untuk panduan:

```python
# Fungsi ini menghitung PPN 10% dari total harga.
# Input: total_harga (float), anggota (bool) untuk diskon 5%.
# Output: total_akhir (float).
def hitung_total(total_harga, anggota):
     # Copilot akan menyarankan: 
     if anggota:
          return total_harga * 0.95 * 1.10
     else:
          return total_harga * 1.10
```

## Bagian 4: Cara GitHub Copilot Memproses Permintaan
1. **Alur Kerja: Dari Prompt ke Kode**  
    - Input & Keamanan:  
      Analogi: Seperti mengirim surat berperangko elektronik. Permintaan dikirim via HTTPS dan difilter dari konten berbahaya.
    - Proses:  
      - Kode dan komentar Anda dikirim dengan enkripsi.  
      - Filter memblokir kode yang mengandung SQL injection atau kata kasar.
    - Pemrosesan Konteks:  
      - Copilot menganalisis:  
         - Kode di sekitar kursor Anda.  
         - Nama file (misal: server.js akan memicu saran Node.js).  
         - Tab terbuka (misal: file components/Button.jsx memengaruhi saran React).
    - Pembuatan Kode dengan LLM:  
      - Model bahasa (LLM) mencari pola dari data latihan (termasuk kode GitHub publik).
      - Contoh: Jika Anda mengetik // hitung faktorial, Copilot menyarankan loop for atau fungsi rekursif.
    - Post-Processing:  
      - Filter menghapus kode yang mirip dengan proyek publik (untuk menghindari plagiarisme).  
      - Pemeriksaan keamanan: Misal, kode yang mengandung eval() mungkin ditandai.

## Bagian 5: Memahami LLM di Balik GitHub Copilot
1. **Apa itu Model Bahasa Besar (LLM)?**  
    Analogi: LLM seperti seorang penulis yang telah membaca seluruh perpustakaan kode dan dokumentasi. Ia tidak menyalin, tetapi memahami pola untuk menulis kode baru.
2. **Fitur LLM**:  
    - Volume Data: Latihan dengan miliaran baris kode dari sumber terbuka.  
    - Fleksibilitas: Bisa beralih dari Python ke JavaScript dalam satu proyek.  
    - Kontekstual: Memahami bahwa render() di React berbeda dengan di Flask.
3. **Penyempurnaan dengan LoRA**  
    - Analogi: LoRA seperti mengajari ahli masak untuk membuat hidangan spesifik tanpa melupakan resep dasar.  
    - Cara Kerja:  
      - Model dasar (misal: GPT-3.5) sudah paham sintaksis umum.  
      - LoRA menambahkan lapisan kecil yang disesuaikan untuk tugas pengkodean.  
      - Hasil: Kode yang lebih presisi untuk kasus seperti pembuatan API atau manajemen state.

## Bagian 6: Studi Kasus & Latihan
1. **Kasus 1: Membangun Fungsi Validasi Email**  
    - Prompt Awal: "Buat fungsi validasi email."  
      Output mungkin melewatkan edge case seperti user.name@domain.co.id.  
    - Prompt Dioptimalkan:

```python
# Fungsi validasi email dengan regex.
# Kriteria: format 'nama@domain.ext', ext 2-3 karakter, domain tidak boleh angka.
import re
def validate_email(email):
     pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,3}$'
     return re.match(pattern, email) is not None
```

2. **Kasus 2: Debugging dengan Copilot**  
    - Permasalahan: Kode berikut error di runtime:

```javascript
function add(a, b) {
     return a + b;
}
console.log(add("5", 3)); // Output: "53"
```

    - Prompt ke Copilot Chat: "Kenapa fungsi add mengembalikan '53' alih-alih 8? Bagaimana memperbaikinya?"  
    - Respons Copilot:  
      - Penyebab: Concatenation string karena input "5" adalah string.  
      - Solusi: Tambahkan konversi ke angka:

```javascript
function add(a, b) {
     return Number(a) + Number(b);
}
```

## Bagian 7: Kesimpulan & Tips Akhir
**Kunci Sukses**:  
- Detail & Konteks: Semakin spesifik, semakin baik.  
- Iterasi: Jangan ragu memperbaiki prompt.  
- Keamanan: Selalu verifikasi kode yang dihasilkan untuk kerentanan.

**Challenge Diri Anda**:  
- Latihan: Gunakan Copilot untuk membuat fungsi Fibonacci dengan batasan waktu eksekusi.  
- Eksperimen: Bandingkan hasil prompt "Buat REST API" dengan "Buat REST API menggunakan Express.js dengan endpoint GET /users dan autentikasi JWT".

**Catatan untuk Pembelajaran**:  
- GitHub Copilot adalah alat, bukan pengganti pemahaman konsep. Selalu pahami kode yang dihasilkan.  
- Manfaatkan mode Chat untuk dialog interaktif saat debugging atau eksplorasi ide.