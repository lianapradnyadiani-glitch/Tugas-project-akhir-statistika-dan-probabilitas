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
  - Di analisis ini saya fokus ke satu variabel utama, yaitu Pendapatan_Tahunan_Miliar_IDR. Dari perhitungan yang dilakukan, didapatkan
    - a. Mean : 31,8831846153846
    - b. Median : 31,305
    - c. Modus : 1,87
  - *Interpretasi:* Jelaskan apa arti dari nilai-nilai tersebut terkait dengan data Anda.
    - Berdasarkan hasil tersebut, dapat diketahui bahwa rata-rata pendapatan tahunan startup SaaS berada di kisaran 31 miliar rupiah. Nilai median yang mendekati mean menunjukkan bahwa
      distribusi data pendapatan relatif seimbang. Namun, nilai modus yang lebih kecil mengindikasikan bahwa pendapatan yang paling sering muncul berada pada tingkat yang rendah. Hal
      ini menunjukkan bahwa sebagian besar startup dalam dataset masih memiliki pendapatan yang relatif kecil, sementara beberapa startup dengan pendapatan sangat tinggi berkontribusi
      terhadap peningkatan nilai rata-rata.
- **Ukuran Sebaran (Standar Deviasi, Range, Kuartil):*
  - Hasil ukuran sebaran untuk Pendapatan_Tahunan_Miliar_IDR adalah:
    - a. Standar deviasi : 19,79
    - b. Range : 65,89
    - c. Kuartil : Q1 = 14,31 dan Q3 = 49,04.
  - *Interpretasi:* Jelaskan seberapa menyebar data Anda berdasarkan nilai-nilai ini.
    - Nilai standar deviasi yang cukup besar menunjukkan bahwa pendapatan antar startup memiliki variasi yang cukup tinggi. Range yang lebar memperlihatkan adanya perbedaan yang
      signifikan antara pendapatan terendah dan tertinggi. Berdasarkan nilai kuartil, dapat dilihat bahwa sebagian startup berada pada tingkat pendapatan yang relatif rendah, sementara
      sebagian lainnya sudah berada pada tingkat pendapatan yang lebih tinggi. Hal ini menunjukkan bahwa distribusi pendapatan dalam dataset tidak merata dan mencerminkan perbedaan
      skala usaha antar startup.
- **Visualisasi (Histogram/Boxplot):**
  - *Sematkan gambar plot dari folder /results...*
     <img width="1366" height="768" alt="Screenshot (126)" src="https://github.com/user-attachments/assets/5174e463-4435-4019-a0f5-bec7e8385045" />
  - *Interpretasi:* Jelaskan wawasan apa yang Anda dapatkan dari bentuk distribusi data.
    - Dari histogram terlihat bahwa distribusi pendapatan menyebar dari nilai rendah hingga tinggi, dengan rata-rata berada di sekitar bagian tengah distribusi. Meskipun demikian, masih
      terdapat nilai ekstrem terutama pada pendapatan yang tinggi. Ini menunjukkan bahwa terdapat beberapa startup dengan pendapatan yang jauh lebih besar dibandingkan mayoritas startup
      lainnya. Visualisasi ini memperkuat hasil analisis sebelumnya bahwa data pendapatan tahunan memiliki sebaran yang cukup luas.

### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - Nilai p-value = 1,497e-14
  - *Interpretasi:* Apakah data Anda terdistribusi normal berdasarkan hasil uji? Apa implikasinya?
    
    - Berdasarkan nilai p-value yang jauh lebih kecil dari 0,05, dapat disimpulkan bahwa data Pendapatan_Tahunan_Miliar_IDR tidak berdistribusi normal. Hal ini berarti data tidak
      memenuhi asumsi normalitas. Implikasinya, hasil analisis yang mengasumsikan distribusi normal perlu diinterpretasikan dengan hati-hati, serta menunjukkan bahwa data pendapatan
      memiliki pola sebaran yang tidak simetris dan dipengaruhi oleh nilai-nilai ekstrem.
- **Plot Q-Q:**
  - *Sematkan gambar plot dari folder /results...*
   <img width="1366" height="768" alt="Screenshot (128)" src="https://github.com/user-attachments/assets/b5e1c2f9-62eb-40e2-9556-73d7350943d3" />
  - *Interpretasi:* Apakah titik-titik data mengikuti garis lurus? Apa artinya?
    - Pada Q-Q plot terlihat bahwa titik-titik data tidak sepenuhnya mengikuti garis lurus, terutama pada bagian awal dan akhir grafik. Penyimpangan ini menunjukkan adanya perbedaan
      antara distribusi data aktual dengan distribusi normal teoritis. Dengan demikian, hasil visualisasi ini memperkuat kesimpulan dari uji Shapiro-Wilk bahwa data pendapatan tahunan
      tidak berdistribusi normal.

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - Nilai r = 0,996
  - *Interpretasi:* Seberapa kuat dan apa arah hubungan antara dua variabel yang Anda uji? (misalnya, korelasi positif kuat, negatif lemah, atau tidak ada korelasi).
    - Nilai korelasi yang mendekati 1 menunjukkan bahwa hubungan antara Pendapatan_Tahunan_Miliar_IDR dan Biaya_Akuisisi_Pelanggan_Juta_IDR bersifat positif dan sangat kuat. Artinya,
      peningkatan pendapatan tahunan startup cenderung diikuti oleh peningkatan biaya akuisisi pelanggan. Hubungan yang sangat kuat ini mengindikasikan bahwa kedua variabel memiliki
      keterkaitan yang tinggi dalam dataset yang dianalisis.
- **Visualisasi (Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
    <img width="1366" height="768" alt="Screenshot (129)" src="https://github.com/user-attachments/assets/53bf7e9a-8020-4b14-a2f4-aac9b59506a9" />
  - *Interpretasi:* Apakah pola pada scatter plot mendukung hasil koefisien korelasi?
    - Berdasarkan scatter plot, terlihat bahwa titik-titik data membentuk pola yang naik dari kiri ke kanan dan sebagian besar mengikuti garis tren linear. Pola ini menunjukkan adanya
      hubungan linear yang konsisten antara kedua variabel. Dengan demikian, visualisasi scatter plot mendukung hasil koefisien korelasi yang menunjukkan bahwa hubungan antara pendapatan
      tahunan dan biaya akuisisi pelanggan sangat kuat dan searah.
    
### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Y = b0 + b1*X*
    - b0 (intercept) = 1,37
    - b1 (slope) = 1,01
    - Y = 1,37 + 1,01X, dengan Y = Pendapatan_Tahunan_Miliar_IDR dan X = Biaya_Akuisisi_Pelanggan_Juta_IDR
  - *Interpretasi:* Jelaskan arti dari koefisien intercept (b0) dan slope (b1) dalam konteks data Anda.
    - Nilai intercept sebesar 1,37 menunjukkan bahwa ketika biaya akuisisi pelanggan bernilai nol, pendapatan tahunan startup diperkirakan berada pada angka 1,37 miliar rupiah. Walaupun
      kondisi ini jarang terjadi secara nyata, nilai tersebut dapat dianggap sebagai titik awal model regresi. Sementara itu, nilai slope sebesar 1,01 menunjukkan bahwa setiap kenaikan
      biaya akuisisi pelanggan sebesar 1 juta rupiah akan diikuti oleh kenaikan pendapatan tahunan sekitar 1,01 miliar rupiah. Hal ini menunjukkan adanya pengaruh positif dari biaya
      akuisisi pelanggan terhadap pendapatan tahunan startup.
- **Evaluasi Model (R-squared):**
  - Nilai R-squared = 0,991 atau 99,1%
  - *Interpretasi:* Berapa persen variasi dari variabel dependen yang dapat dijelaskan oleh model regresi Anda?
    - Nilai R-squared sebesar 99,1% menunjukkan bahwa sebagian besar variasi pada variabel pendapatan tahunan dapat dijelaskan oleh variabel biaya akuisisi pelanggan dalam model regresi
      ini. Dengan kata lain, model regresi yang dibangun memiliki kemampuan yang sangat baik dalam menjelaskan hubungan antara kedua variabel, sedangkan sisanya yang sangat kecil
      dipengaruhi oleh faktor lain di luar model.
- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
    <img width="1366" height="768" alt="Screenshot (130)" src="https://github.com/user-attachments/assets/2334dee1-5cb5-4fb0-9822-be5a7af7dcf9" />
  - *Interpretasi:* Jelaskan bagaimana garis regresi merepresentasikan hubungan antara variabel.
    - Pada scatter plot terlihat bahwa garis regresi membentuk pola garis lurus yang menanjak dan berada sangat dekat dengan titik-titik data. Hal ini menunjukkan bahwa hubungan antara
      biaya akuisisi pelanggan dan pendapatan tahunan bersifat linear dan konsisten. Kedekatan titik-titik data dengan garis regresi juga menandakan bahwa model regresi mampu
      merepresentasikan hubungan antar variabel dengan cukup baik.
      
---

## 6. Kesimpulan

Rangkum temuan utama dari analisis Anda dalam beberapa kalimat. Apa wawasan paling penting yang Anda peroleh?
- Berdasarkan seluruh tahapan analisis yang telah dilakukan, saya menemukan bahwa pendapatan tahunan startup SaaS memiliki variasi yang cukup besar dan tidak terdistribusi secara
  normal. Hasil statistik deskriptif menunjukkan adanya perbedaan yang signifikan antara startup dengan pendapatan rendah dan tinggi, yang mengindikasikan perbedaan skala usaha dalam
  dataset. Selain itu, uji normalitas dan visualisasi juga memperkuat bahwa data pendapatan dipengaruhi oleh beberapa nilai ekstrem.
  Saya juga menemukan adanya hubungan yang sangat kuat
  dan positif antara biaya akuisisi pelanggan dan pendapatan tahunan startup, yang ditunjukkan oleh nilai koefisien korelasi yang mendekati satu. Hasil analisis regresi linear sederhana
  menunjukkan bahwa biaya akuisisi pelanggan memiliki pengaruh positif yang signifikan terhadap pendapatan tahunan, di mana peningkatan biaya akuisisi diikuti oleh peningkatan
  pendapatan. Dengan nilai R-squared yang sangat tinggi, model regresi yang dibangun mampu menjelaskan sebagian besar variasi pendapatan tahunan startup. Secara keseluruhan, analisis
  ini memberikan wawasan bahwa strategi pengeluaran untuk akuisisi pelanggan memiliki peran penting dalam meningkatkan pendapatan startup SaaS.
