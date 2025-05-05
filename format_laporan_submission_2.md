# Laporan Proyek Machine Learning - Laila Dwi Kartika Sari

## Project Overview

Netflix adalah salah satu platform streaming terbesar di dunia yang menawarkan ribuan judul film dan acara TV. Dengan banyaknya konten yang tersedia, pengguna seringkali kesulitan menemukan konten yang sesuai dengan preferensi mereka. Sistem rekomendasi yang efektif dapat membantu pengguna menemukan konten yang relevan, meningkatkan kepuasan pengguna, dan meningkatkan engagement di platform. Proyek ini bertujuan untuk membangun sistem rekomendasi berbasis konten untuk Netflix menggunakan dataset yang berisi informasi tentang film dan acara TV yang tersedia di platform tersebut.

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

**Exploratory Data Analysis (EDA) 

- Deskripsi Variabel**
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
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

## Reverensi
- Format Referensi dapat mengacu pada penulisan sitasi [IEEE](https://journals.ieeeauthorcenter.ieee.org/wp-content/uploads/sites/7/IEEE_Reference_Guide.pdf), [APA](https://www.mendeley.com/guides/apa-citation-guide/) atau secara umum seperti [di sini](https://penerbitdeepublish.com/menulis-buku-membuat-sitasi-dengan-mudah/)
- Sumber yang bisa digunakan [Scholar](https://scholar.google.com/)