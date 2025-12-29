<img width="1366" height="768" alt="Screenshot (126)" src="https://github.com/user-attachments/assets/37f54ca2-4929-439a-9220-fc942b0334ae" /># Tugas Analisis Statistik: Deskriptif, Korelasi, dan Regresi

## 1. Informasi Penyusun

- **Nama:** NI MADE LIANA PRADNYADIANI
- **NIM:** 2515091029
- **Program Studi:** SISTEM INFORMASI
- **Mata Kuliah:** Statistika dan Probabilitas

---

## 2. Deskripsi Proyek

Data yang digunakan dalam proyek ini berasal dari file data_startup_saas.csv yang berisi data tentang startup SaaS, seperti kategori layanan, pendapatan tahunan, biaya akuisisi pelanggan, nilai pelanggan, dan tingkat churn. Dari semua variabel yang ada, pada proyek ini hanya menggunakan dua variabel, yaitu Pendapatan_Tahunan_Miliar_IDR dan Biaya_Akuisisi_Pelanggan_Juta_IDR. Tujuan melakukan analisis ini untuk mengetahui gambaran umum data pendapatan melalui statistik deskriptif, melihat hubungan antara pendapatan tahunan dengan biaya akuisisi pelanggan menggunakan analisis korelasi, serta membuat model regresi linear sederhana untuk mengetahui pengaruh biaya akuisisi pelanggan terhadap pendapatan tahunan startup.

---

## 3. Struktur Proyek

Proyek ini diorganisir ke dalam beberapa folder:
- `/data`: Berisi dataset mentah yang digunakan untuk analisis.
- `/scripts`: Berisi semua skrip R yang digunakan dalam analisis, diurutkan berdasarkan alur kerja.
- `/results`: Berisi output dari analisis, seperti plot, gambar, atau tabel ringkasan.

---

## 4. Cara Menjalankan Analisis

Untuk mereproduksi hasil analisis ini, ikuti langkah-langkah berikut:
1. Pastikan Anda memiliki R dan RStudio terinstal.
2. Buka proyek R ini di RStudio.
3. Instal paket yang diperlukan dengan menjalankan perintah berikut di konsol R:
   ```R
   # install.packages(c("tidyverse", "corrplot", "knitr"))
   ```
4. Jalankan skrip di dalam folder `/scripts` secara berurutan, mulai dari `01_data_preparation.R` hingga `05_analisis_regresi.R`.

---

## 5. Hasil dan Interpretasi

Di bagian ini, mahasiswa diharapkan untuk menyajikan dan menginterpretasikan hasil dari setiap tahap analisis.

### 5.1. Statistik Deskriptif
- **Ukuran Pemusatan (Mean, Median, Modus):**
  - *Tabel atau ringkasan...*
  - Di analisis ini saya fokus ke satu variabel utama, yaitu Pendapatan_Tahunan_Miliar_IDR. Dari perhitungan yang dilakukan, didapatkan:
a. Mean : 31,8831846153846
b. Median : 31,305
c. Modus : 1,87
  - *Interpretasi:* Jelaskan apa arti dari nilai-nilai tersebut terkait dengan data Anda.
  - Dari hasil perhitungan, rata-rata pendapatan tahunan startup SaaS berada di angka 31,8831846153846. Ini gambaran umum seberapa besar skala bisnis startup dalam dataset. Nilai median
    sebesar 31,305 yang hampir sama dengan mean menunjukkan bahwa data pendapatan cukup seimbang dan tidak terlalu condong ke satu sisi. Namun, nilai modus yang hanya 1,87 menunjukkan
    bahwa pendapatan yang paling sering muncul justru berada di angka yang relatif rendah. Ini mengindikasikan bahwa meskipun secara rata-rata pendapatan terlihat cukup tinggi,
    kenyataannya banyak startup yang masih berada di tahap awal dengan pendapatan kecil, sementara beberapa startup besar dengan pendapatan sangat tinggi ikut mendorong nilai rata-rata
    menjadi besar.
- **Ukuran Sebaran (Standar Deviasi, Range, Kuartil):**
  - *Tabel atau ringkasan...*
  - Hasil ukuran sebaran untuk Pendapatan_Tahunan_Miliar_IDR adalah:
a. Standar deviasi : 19,79
b. Range : 65,89
c. Kuartil : Min = 1,00, Q1 = 14,31, Median = 31,305, Mean = 31,8831846153846, Q3 = 49,04, Max = 66,89
  - *Interpretasi:* Jelaskan seberapa menyebar data Anda berdasarkan nilai-nilai ini.
  - Nilai standar deviasi sebesar 19,79 menunjukkan bahwa pendapatan antar startup cukup bervariasi dan tidak berkumpul di sekitar nilai rata-rata saja. Range yang mencapai 65,89
    memperlihatkan adanya selisih yang jauh antara startup dengan pendapatan terendah dan tertinggi. Dari nilai kuartil terlihat bahwa sekitar 25% startup memiliki pendapatan di bawah
    14,31, sementara 25% lainnya sudah berada di atas 49,04. Ini menandakan bahwa tingkat pendapatan antar startup dalam dataset sangat beragam, sehingga bisa disimpulkan bahwa kondisi
    bisnis startup SaaS di data ini tidak homogen dan mencerminkan perbedaan skala usaha yang cukup lebar.
- **Visualisasi (Histogram/Boxplot):**
  - *Sematkan gambar plot dari folder /results...*
  - <img width="1366" height="768" alt="Screenshot (126)" src="https://github.com/user-attachments/assets/5174e463-4435-4019-a0f5-bec7e8385045" />
  - *Interpretasi:* Jelaskan wawasan apa yang Anda dapatkan dari bentuk distribusi data.
  - Dari histogram terlihat bahwa data pendapatan menyebar dari nilai kecil sampai besar, dengan konsentrasi terbesar berada di sekitar nilai tengah. Walaupun rata-rata berada di tengah
    distribusi, masih terlihat adanya nilai ekstrem di sisi bawah maupun atas. Hal ini menunjukkan bahwa ada startup dengan pendapatan yang jauh lebih kecil atau jauh lebih besar
    dibandingkan mayoritas. Kondisi ini memperkuat hasil sebelumnya bahwa sebaran pendapatan cukup lebar dan tidak hanya terpusat pada satu kelompok nilai saja.

### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - *Nilai p-value...*
  - *Interpretasi:* Apakah data Anda terdistribusi normal berdasarkan hasil uji? Apa implikasinya?
- **Plot Q-Q:**
  - *Sematkan gambar plot dari folder /results...*
  - *Interpretasi:* Apakah titik-titik data mengikuti garis lurus? Apa artinya?

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - *Nilai r...*
  - *Interpretasi:* Seberapa kuat dan apa arah hubungan antara dua variabel yang Anda uji? (misalnya, korelasi positif kuat, negatif lemah, atau tidak ada korelasi).
- **Visualisasi (Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - *Interpretasi:* Apakah pola pada scatter plot mendukung hasil koefisien korelasi?

### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Y = b0 + b1*X*
  - *Interpretasi:* Jelaskan arti dari koefisien intercept (b0) dan slope (b1) dalam konteks data Anda.
- **Evaluasi Model (R-squared):**
  - *Nilai R-squared...*
  - *Interpretasi:* Berapa persen variasi dari variabel dependen yang dapat dijelaskan oleh model regresi Anda?
- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - *Interpretasi:* Jelaskan bagaimana garis regresi merepresentasikan hubungan antara variabel.

---

## 6. Kesimpulan

Rangkum temuan utama dari analisis Anda dalam beberapa kalimat. Apa wawasan paling penting yang Anda peroleh?
