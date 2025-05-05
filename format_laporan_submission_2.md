# Laporan Proyek Machine Learning - Laila Dwi Kartika Sari

## Project Overview

Netflix adalah salah satu platform streaming terbesar di dunia yang menawarkan ribuan judul film dan acara TV. Dengan banyaknya konten yang tersedia, pengguna seringkali kesulitan menemukan konten yang sesuai dengan preferensi mereka. Sistem rekomendasi yang efektif dapat membantu pengguna menemukan konten yang relevan, meningkatkan kepuasan pengguna, dan meningkatkan engagement di platform [1](https://help.netflix.com/id/node/100639). Proyek ini bertujuan untuk membangun sistem rekomendasi berbasis konten untuk Netflix menggunakan dataset yang berisi informasi tentang film dan acara TV yang tersedia di platform tersebut.

## Business Understanding


### Problem Statements

Pengguna Netflix seringkali kesulitan menemukan konten yang sesuai dengan preferensi mereka karena banyaknya pilihan yang tersedia.

### Goals

Membangun sistem rekomendasi yang dapat menyarankan konten serupa berdasarkan deskripsi dan fitur lainnya.

### Solution statements

solusi yang diterapkan pada pengerjaan proyek sistem rekomendasi kali ini yaitu dengan menerapkan algoritma **content based filtering** 

- ***content based filtering***.
        pada tahap pengembangan model dengan model dengan metode content base filtering ini yaitu merekomendasikan item yang mirip dengan item yang disukai pengguna di masa lalu. Content-based filtering mempelajari profil minat pengguna baru berdasarkan data dari objek yang telah dinilai pengguna. Algoritma ini bekerja dengan menyarankan item serupa yang pernah disukai di masa lalu atau sedang dilihat di masa kini kepada pengguna. Semakin banyak informasi yang diberikan pengguna, semakin baik akurasi sistem rekomendasi.

## Data Understanding

**Informasi Dataset** 
Informasi   | Keterangan 
----------- |------------------
Link        | https://www.kaggle.com/datasets/anandshaw2001/netflix-movies-and-tv-shows
Lisensi     | CC0: Public Domain
Size        | 3.4 MB

**Exploratory Data Analysis (EDA)**

**Deskripsi Variabel**

Dataset yang digunakan dalam proyek ini adalah "Netflix Movies and TV Shows" yang dapat diunduh dari Kaggle. Dataset [kaggle](https://www.kaggle.com/datasets/anandshaw2001/netflix-movies-and-tv-shows), terdapat 2 tipe data pada variabel-variabel netflix_titles dataset yaitu

tipe data int :
- *release_year* : Tahun judul tersebut pertama kali dirilis

tipe data object.
- *show_id* : Pengenal unik untuk setiap pertunjukan (s1, s2)
- *type* : Menentukan apakah judulnya adalah "Film" atau "Acara TV"
- *title* : Nama judul Netflix
- *director* : Sutradara judulnya
- *cast* : Aktor utama yang terlibat dalam judul
- *country* : Negara tempat judul tersebut diproduksi
- *date_added* : Tanggal saat judul ditambahkan ke Netflix
- *rating* : Peringkat konten ("PG-13", "TV-MA")
- *duration* : Durasi film (dalam menit) atau jumlah musim acara TV
- *listed_in* : Kategori atau genre yang dicakup judul ("Dokumenter", "Drama TV")
- *description* : Deskripsi ringkasan

Dataset ini berisi 8807 entri dengan 12 fitur. Setelah dilakukan pembersihan data, fitur yang digunakan adalah:
- *type* : Menentukan apakah judulnya adalah "Film" atau "Acara TV"
- *title* : Nama judul Netflix
- *rating* : Peringkat konten ("PG-13", "TV-MA")
- *duration* : Durasi film (dalam menit) atau jumlah musim acara TV
- *description* : Deskripsi ringkasan

## Data Preparation

 - **Mengecek Missing value**
    Tujuannya dilakukan proses missing value agar dataset menjadi bersih dari fitur fitur yang valuenya kosong karena dapat menimbulkan hasil akurasi yang kurang baik ataupun hasil bias. untuk mengecek missing value menggunakan fitur *isnull* dan juga fitur *sum()* untuk melihat jumlah data.pada saat fitur itu dijalankan maka akan di cek semua data yang berisi missing value pada dataset. setelah dilakukan pengencekan missing valeu ternyata banyak data missing.sebelum menghapus missing value pada data. terlebih dahulu hapus fitur yang tidak akan di gunakan pada sistem rekomendasi. setelah fitur telah di hapus maka di lakukan penghapusan missing value pada data yang akan di gunakan untuk sistem rekomendasi.

- **Membuat variabel preparation**
    Membuat variabel preparation yang berisi dataframe netflix_clean kemudian mengurutkan berdasarkan title. kemudian membuang data duplikat pada variable preparation. karena akan menggunakan data unik untuk dimasukkan ke dalam proses pemodelan. pada proyek kali ini akan membuang duplikat data berdasarkan fitur title.

- **Mengonversi data series menjadi dalam bentuk list**
    konversi variable-variable seperti type, title, rating, duration dan description menjadi bentuk list

- **Membuat dictionary pada data**
    Tujuan pembuatan Dictionary ini agar model yang dibuat hanya memprediksi hasil dari fitur fitur yang hanya digunakan sebagai fitur untuk melakukan proses rekomendasi. pada proyek kali ini data ‘netflix_type’, ‘netflix_title’, ‘netflix_rating’, ‘netflix_duration’, dan ‘netflix_description’ akan dijadikan dictionary ‘netflix_clear’

## Modeling
Pada tahap pengembang model development pada studi kasus rekomendasi buku ini  menerapkan metode content base filtering yaitu dimana dengan menerapkan metode ini diharapkan model mampu menghasilkan sebuah hasil rekemendasi berdasarkan hasil permasalahn yang ada. 
- Kelemahan dari metode content-based filtering adalah terbatasnya rekomendasi hanya pada item-item yang mirip sehingga tidak ada kesempatan untuk mendapatkan item yang tidak terduga.
- Kelebihan metode content-based filtering antara lain tidak memerlukan data pengguna lain sehingga cocok untuk pengguna baru, mampu memberikan rekomendasi yang spesifik dan relevan berdasarkan kemiripan fitur konten seperti deskripsi atau genre, serta memiliki transparansi tinggi karena alasan rekomendasi dapat dengan mudah dipahami. 

Model ini merekomendasikan konten berdasarkan kemiripan deskripsi menggunakan TF-IDF Vectorizer dan cosine similarity. Langkah-langkahnya:

1. **TF-IDF Vectorizer**: Mengubah deskripsi menjadi vektor numerik.
    - parameter : 
    `````
    tf = TfidfVectorizer(max_df=0.8, min_df=0.02, ngram_range=(1,2))
    `````

    Keterangan : max_df=0.8: Mengabaikan istilah yang muncul di lebih dari 80% dokumen. min_df=0.02: Mengabaikan istilah yang muncul di kurang dari 2% dokumen. ngram_range=(1,2): Mempertimbangkan unigram dan bigram (kombinasi 1 dan 2 kata).

2. **Cosine Similarity**: Menghitung kemiripan antara konten berdasarkan vektor deskripsi.
    - parameter :
    `````
    Cosine Similarity tidak memiliki parameter yang dapat diatur secara langsung. Ia menghitung kemiripan berdasarkan matriks TF-IDF yang telah dibuat sebelumnya.
    `````

## Evaluation
Metrik evaluasi yang digunakan adalah precision@k, yang mengukur proporsi rekomendasi yang relevan dari total rekomendasi yang diberikan. Formula:
![Gambar](https://github.com/lailadwikartikasari/Sistem-Rekomendasi/blob/main/image/2.png?raw=true)
- Jika dari 5 rekomendasi, 3 di antaranya relevan, maka precision@5 = 3/5 = 0.6.

Hasil Dari Evaluasi
![hasil evaluasi](https://github.com/lailadwikartikasari/Sistem-Rekomendasi/blob/main/image/1.png?raw=true)
Hasil evaluasi menunjukkan bahwa model content-based filtering dapat memberikan rekomendasi yang cukup relevan berdasarkan deskripsi konten. Namun, untuk meningkatkan akurasi, dapat dipertimbangkan penggunaan collaborative filtering atau hybrid approach.


**---Ini adalah bagian akhir laporan---**
