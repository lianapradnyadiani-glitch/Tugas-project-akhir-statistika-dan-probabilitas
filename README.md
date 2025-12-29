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
  - Di analisis ini saya fokus ke satu variabel utama, yaitu Pendapatan_Tahunan_Miliar_IDR. Dari perhitungan yang dilakukan, didapatkan
    - a. Mean : 31,8831846153846
    - b. Median : 31,305
    - c. Modus : 1,87
  - *Interpretasi:* Jelaskan apa arti dari nilai-nilai tersebut terkait dengan data Anda.
  - Dari hasil perhitungan, rata-rata pendapatan tahunan startup SaaS berada di angka 31,8831846153846. Ini gambaran umum seberapa besar skala bisnis startup dalam dataset. Nilai median
    sebesar 31,305 yang hampir sama dengan mean menunjukkan bahwa data pendapatan cukup seimbang dan tidak terlalu condong ke satu sisi. Namun, nilai modus yang hanya 1,87 menunjukkan
    bahwa pendapatan yang paling sering muncul justru berada di angka yang relatif rendah. Ini mengindikasikan bahwa meskipun secara rata-rata pendapatan terlihat cukup tinggi,
    kenyataannya banyak startup yang masih berada di tahap awal dengan pendapatan kecil, sementara beberapa startup besar dengan pendapatan sangat tinggi ikut mendorong nilai rata-rata
    menjadi besar.
- **Ukuran Sebaran (Standar Deviasi, Range, Kuartil):**
  - *Tabel atau ringkasan...*
  - Hasil ukuran sebaran untuk Pendapatan_Tahunan_Miliar_IDR adalah:
    - a. Standar deviasi : 19,79
    - b. Range : 65,89
    - c. Kuartil : Min = 1,00, Q1 = 14,31, Median = 31,305, Mean = 31,8831846153846, Q3 = 49,04, Max = 66,89
  - *Interpretasi:* Jelaskan seberapa menyebar data Anda berdasarkan nilai-nilai ini.
  - Nilai standar deviasi sebesar 19,79 menunjukkan bahwa pendapatan antar startup cukup bervariasi dan tidak berkumpul di sekitar nilai rata-rata saja. Range yang mencapai 65,89
    memperlihatkan adanya selisih yang jauh antara startup dengan pendapatan terendah dan tertinggi. Dari nilai kuartil terlihat bahwa sekitar 25% startup memiliki pendapatan di bawah
    14,31, sementara 25% lainnya sudah berada di atas 49,04. Ini menandakan bahwa tingkat pendapatan antar startup dalam dataset sangat beragam, sehingga bisa disimpulkan bahwa kondisi
    bisnis startup SaaS di data ini tidak homogen dan mencerminkan perbedaan skala usaha yang cukup lebar.
- **Visualisasi (Histogram/Boxplot):**
  - *Sematkan gambar plot dari folder /results...*
     <img width="1366" height="768" alt="Screenshot (126)" src="https://github.com/user-attachments/assets/5174e463-4435-4019-a0f5-bec7e8385045" />
  - *Interpretasi:* Jelaskan wawasan apa yang Anda dapatkan dari bentuk distribusi data.
  - Dari histogram terlihat bahwa data pendapatan menyebar dari nilai kecil sampai besar, dengan konsentrasi terbesar berada di sekitar nilai tengah. Walaupun rata-rata berada di tengah
    distribusi, masih terlihat adanya nilai ekstrem di sisi bawah maupun atas. Hal ini menunjukkan bahwa ada startup dengan pendapatan yang jauh lebih kecil atau jauh lebih besar
    dibandingkan mayoritas. Kondisi ini memperkuat hasil sebelumnya bahwa sebaran pendapatan cukup lebar dan tidak hanya terpusat pada satu kelompok nilai saja.

### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - Nilai p-value = 1,497e-14
  - *Interpretasi:* Apakah data Anda terdistribusi normal berdasarkan hasil uji? Apa implikasinya?
  - Nilai p-value yang jauh di bawah 0,05 menunjukan kalau data pendapatan tahunan tidak berdistribusi normal. Dengan kata lain, pola datanya tidak ngikutin bentuk lonceng yang ideal.
    Ini penting untuk diperhatikan karena beberapa analisis statistik biasanya ngasumsikan data normal. Jadi, dari hasil ini bisa dibilang kalau data pendapatan startup punya sebaran
    yang tidak simetris dan mungkin dipengaruhi sama nilai-nilai ekstrem.
- **Plot Q-Q:**
  - *Sematkan gambar plot dari folder /results...*
   <img width="1366" height="768" alt="Screenshot (128)" src="https://github.com/user-attachments/assets/b5e1c2f9-62eb-40e2-9556-73d7350943d3" />
  - *Interpretasi:* Apakah titik-titik data mengikuti garis lurus? Apa artinya?
  - Di Q-Q plot kelihatan kalau titik-titiknya tidak nempel di garis lurus, apalagi di bagian ujung grafik. Penyimpangan ini nunjukin kalau data punya pola yang beda dari distribusi
    normal. Hasil ini makin nguatkan kalau data pendapatan tahunan memang tidak normal, sesuai sama hasil uji Shapiro-Wilk sebelumnya

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - Nilai r = 0,996
  - *Interpretasi:* Seberapa kuat dan apa arah hubungan antara dua variabel yang Anda uji? (misalnya, korelasi positif kuat, negatif lemah, atau tidak ada korelasi).
  - Nilai korelasi sebesar 0,996 itu menunjukan kalau hubungan antara pendapatan tahunan dan biaya akuisisi pelanggan itu positif dan sangat kuat. Artinya, kalau pendapatan startup
    makin besar, biasanya biaya yang dikeluarin buat dapetin pelanggan juga ikut naik. Hubungan yang kuat ini masuk akal, karena startup yang skala bisnisnya besar biasanya butuh
    strategi pemasaran yang lebih intens dan biaya yang lebih tinggi juga.
- **Visualisasi (Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
    <img width="1366" height="768" alt="Screenshot (129)" src="https://github.com/user-attachments/assets/53bf7e9a-8020-4b14-a2f4-aac9b59506a9" />
  - *Interpretasi:* Apakah pola pada scatter plot mendukung hasil koefisien korelasi?
  - Dari scatter plot, kelihatan pola titik yang naik dari kiri ke kanan dan cukup rapat ngikutin garis tren. Ini menunjukan kalau hubungan kedua variabel itu konsisten dan cenderung
    linear. Jadi, secara visual juga bisa dilihat kalau data mendukung hasil korelasi yang bilang kalau hubungan keduanya memang kuat.

### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Y = b0 + b1*X*
    - b0 (intercept) = 1,37
    - b1 (slope) = 1,01
    - Y = 1,37 + 1,01X, dengan Y = Pendapatan_Tahunan_Miliar_IDR dan X = Biaya_Akuisisi_Pelanggan_Juta_IDR
  - *Interpretasi:* Jelaskan arti dari koefisien intercept (b0) dan slope (b1) dalam konteks data Anda.
  - Dari persamaan regresi di atas, nilai intercept sebesar 1,37 bisa diartikan sebagai perkiraan pendapatan tahunan startup ketika biaya akuisisi pelanggan bernilai nol. Walaupun
    kondisi ini jarang terjadi di dunia nyata, nilai tersebut tetap bisa dianggap sebagai titik awal model. Sementara itu, nilai slope sebesar 1,01 menunjukkan bahwa setiap kenaikan
    biaya akuisisi pelanggan sebesar 1 juta rupiah diperkirakan akan diikuti kenaikan pendapatan tahunan sekitar 1,01 miliar rupiah. Koefisien yang bernilai positif ini menandakan bahwa
    hubungan antara biaya akuisisi dan pendapatan bersifat searah, yaitu semakin besar biaya yang dikeluarkan untuk mendapatkan pelanggan, maka pendapatan startup juga cenderung
    meningkat.
- **Evaluasi Model (R-squared):**
  - Nilai R-squared = 0,991 atau 99,1%
  - *Interpretasi:* Berapa persen variasi dari variabel dependen yang dapat dijelaskan oleh model regresi Anda?
  - Nilai R-squared sebesar 0,991 berarti sekitar 99,1% variasi pada Pendapatan_Tahunan_Miliar_IDR dapat dijelaskan oleh variabel Biaya_Akuisisi_Pelanggan_Juta_IDR dalam model regresi
    ini. Angka ini tergolong sangat tinggi, sehingga bisa dikatakan bahwa model memiliki kemampuan yang sangat baik dalam menjelaskan hubungan antara kedua variabel. Dengan kata lain,
    perubahan pendapatan tahunan startup dalam dataset ini sebagian besar dipengaruhi oleh perubahan biaya akuisisi pelanggan, sementara sisanya yang kecil dipengaruhi oleh faktor lain
    diluar model.
- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
    <img width="1366" height="768" alt="Screenshot (130)" src="https://github.com/user-attachments/assets/2334dee1-5cb5-4fb0-9822-be5a7af7dcf9" />
  - *Interpretasi:* Jelaskan bagaimana garis regresi merepresentasikan hubungan antara variabel.
  - Pada scatter plot terlihat bahwa garis regresi membentuk garis lurus yang menanjak dan berada sangat dekat dengan titik-titik data. Ini menunjukkan bahwa hubungan antara biaya
    akuisisi pelanggan dan pendapatan tahunan bersifat linear dan cukup konsisten. Sebagian besar titik yang menempel di sekitar garis regresi menandakan bahwa prediksi model cukup
    akurat dan kesalahannya relatif kecil. Secara keseluruhan, garis regresi ini merepresentasikan dengan baik bahwa semakin besar biaya akuisisi pelanggan yang dikeluarkan startup,
    maka pendapatan tahunan yang diperoleh juga cenderung semakin besar.

---

## 6. Kesimpulan

Rangkum temuan utama dari analisis Anda dalam beberapa kalimat. Apa wawasan paling penting yang Anda peroleh?
- Dari seluruh analisis yang sudah saya lakukan, saya menemukan kalau pendapatan tahunan startup SaaS di data ini cukup beragam dan sebarannya tidak normal. Saya juga menemukan kalau
  hubungan antara biaya akuisisi pelanggan dan pendapatan itu positif dan sangat kuat. Lewat model regresi, terlihat bahwa biaya akuisisi pelanggan punya pengaruh besar terhadap naik
  turunnya pendapatan startup. Wawasan paling penting yang saya dapat adalah bahwa semakin besar biaya yang dikeluarkan untuk mendapatkan pelanggan, biasanya pendapatan startup juga
  ikut meningkat. Jadi, menurut saya, strategi dalam mengatur biaya akuisisi pelanggan itu penting banget karena sangat berpengaruh ke perkembangan dan skala bisnis startup SaaS.
