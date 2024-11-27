# Laporan Proyek Machine Learning - Lulu Nadhiatun Anisa

## Project Overview
![Film](https://github.com/user-attachments/assets/79169bc0-4e92-4d67-9e9d-d8c40e0462c6)

Di era digital, informasi yang tersedia  dan dapat diakses melalui internet kapanpun dan dimanapun setiap harinya.
Dalam dunia bisnis modern, informasi telah menjadi kebutuhan utama, dengan penggunaan basis data sebagai kunci untuk menghasilkan solusi bisnis yang inovatif. 
Banyak company kini memanfaatkan data untuk memahami preferensi pelanggan, yang pada akhirnya mendorong perkembangan sistem rekomendasi. 
Sistem ini menjadi alat penting untuk meningkatkan pengalaman pengguna dengan menyediakan rekomendasi yang relevan dan sesuai dengan kebutuhan mereka.[[1](https://www.antaranews.com/berita/1776245/layanan-streaming-tantangan-dan-peluang-perfilman-indonesia#google_vignette)]

Maraknya layanan streaming seperti Netflix, Disney Plus, WeTV, dan platform serupa telah menciptakan tren baru dalam pola menonton film, seperti binge-watching dan hopping. 
Tren ini mengacu pada kebiasaan menonton film secara berurutan tanpa jeda.Dengan semakin banyaknya konten dan pilihan genre yang tersedia, 
penyedia layanan streaming dihadapkan pada tantangan untuk memberikan rekomendasi yang relevan agar dapat meningkatkan kepuasan serta loyalitas pengguna.[[2](https://kumparan.com/millennial/mengenal-istilah-binge-watching-dan-hopping-yang-jadi-tren-terbaru-nonton-film-1wREvjSoXeB)]

Dari permasalhan tersebut, proyek ini bertujuan untuk mengembangkan model machine learning yang mendukung sistem rekomendasi film.
Model ini dirancang dengan memanfaatkan data preferensi pengguna berdasarkan histori kesukaan mereka sebelumnya, serta penilaian atau rating dari berbagai pengguna terhadap film tertentu. 
Dengan pendekatan ini, sistem rekomendasi yang dihasilkan diharapkan mampu memberikan rekomendasi yang lebih personal dan akurat, sehingga membantu pengguna menemukan film yang sesuai dengan minat mereka.

## Business Understanding
Pengembangan model sistem rekomendasi film memiliki berbagai manfaat, baik bagi pengguna maupun penyedia layanan seperti efisiensi pencarian, ekplorasi kontenbaru,
peningkatan loyalisat pengguna, optimasi pendapatan dan lainnya.

### Problem Statements
Berdasarkan latar belakang yang telah dijelaskan, berikut adalah rincian masalah yang dapat diatasi melalui proyek ini:
- Bagaimana cara membuat sistem rekomendasi film yang memungkinkan film yang disukai oleh satu pengguna dapat direkomendasikan kepada pengguna lain dengan preferensi serupa?
- Bagaimana cara menyajikan sistem rekomendasi film berdasarkan ratings film tertinggi?

### Goals
Mampu merancang dan mengembangkan sistem rekomendasi yang secara akurat menyarankan konten berdasarkan analisis mendalam terhadap 
rating yang diberikan pengguna serta aktivitas mereka di masa lalu. 

### Solution approach

Solusi yang saya kembangkan menggunakan dua algoritma machine learning untuk mendukung sistem rekomendasi, yaitu:

- **Content Based Filtering** adalah salah satu metode dalam sistem rekomendasi yang digunakan untuk memberikan rekomendasi kepada pengguna berdasarkan karakteristik atau atribut dari item yang telah mereka interaksikan atau sukai sebelumnya.
- **Collaborative Filtering**. adalah teknik yang digunakan dalam sistem rekomendasi untuk memberikan rekomendasi berdasarkan preferensi atau interaksi pengguna lain. Pendekatan ini tidak bergantung pada atribut atau konten dari item itu sendiri (seperti dalam Content-Based Filtering).
  
Algoritma *Content Based Filtering* digunakan untuk merekemondesikan movie berdasarkan aktivitas pengguna pada masa lalu, sedangkan algoritma *Collabarative Filltering* digunakan untuk merekomendasikan movie berdasarkan ratings yang paling tinggi.

## Data Understanding
**Informasi Datasets**

| Jenis | Keterangan |
| ------ | ------ |
| Title | Movie Recommendation Data |
| Source | [Kaggle](https://www.kaggle.com/datasets/rohan4050/movie-recommendation-data) |
| Maintainer | [Rohan Sharma⚡](https://www.kaggle.com/rohan4050) |
| License | Unknown |
| Visibility | Publik |
| Tags | Movie and TV Show, Recommender System |
| Usability | 7.94 |

### Variabel-variabel pada dataset:
Pada file `movies.csv` berisi daftar film yang memiliki 9742 data dan 3 feature:

- `movieId` : memuat nomor ID film  
- `title` : memuat judul film
- `genres` : memuat genre film

Pada file `ratings.csv` berisi daftar ratings atau penilaian terhadap satu film yang memiliki 100836 data dan 4 feature:

- `userId` : memuat nomor ID users
- `movieId` : memuat nomor ID film  
- `rating` : memuat rating atau penilaian films dalam skala bintang, dengan peningkatan setengah bintang dalam rentang 0,5 - 5 bintang
- `timestamp` : memuat kode timestamp

Pada file `tags.csv` berisi daftar tags pada film yang diberikan users yang memiliki 3683 data dan 4 feature:

- `userId` : memuat nomor ID users
- `movieId` : memuat nomor ID film  
- `tag` : memuat tag film
- `timestamp` : memuat kode timestamp

Pada file `links.csv` berisi daftar links film yang mengarah ke laman website films yang memiliki 9742 dan 3 feature: 

- `movieId` : memuat nomor ID film yang merujuk pada website MovieLens
- `imdbId` : memuat nomor ID film yang merujuk pada website IMDb
- `tmdbId` : memuat nomor ID film yang merujuk pada website TMDB

### Exploratory Data Analysis (EDA)

Proses eksplorasi data (Exploratory Data Analysis/EDA) dilakukan dengan menganalisis dataset secara mendalam untuk memperoleh pemahaman yang komprehensif mengenai karakteristik data, sehingga dapat mengungkapkan insight dan pengetahuan (knowledge).

**Univariate Analysis**

Merging Data adalah proses menggabungkan dua atau lebih set data yang memiliki atribut atau kolom yang relevan, untuk membentuk satu dataset yang konsisten dan utuh. Tujuan dari merging data adalah untuk mengintegrasikan informasi yang tersebar dalam berbagai sumber atau tabel sehingga dapat digunakan dalam analisis atau pemodelan. Berikut ini beberapa tahapan yang dilakukan untuk dalam tahapan merging data yang saya lakukan yaitu:
- Menggabungkan beberapa file dengan fungsi `np.concatenate` berdasarkan pada movieId dengan menyimpanya pada variabel `movie_all`

  ![1](https://github.com/user-attachments/assets/5b19ee23-45e0-4ef6-970f-9d672432c3f7)

- Menggabungkan beberapa file dengan fungsi `np.concatenate` berdasarkan pada userId dengan menyimpanya pada variabel `user_all`

  ![2](https://github.com/user-attachments/assets/01988124-1995-4ff4-be25-e95d4f80ded9)

- Menggabungkan beberapa file seperti `links`, `movies`, `ratings`, dan `tags` dengan menyimpannya pada variabel `movie_info`

  ![3](https://github.com/user-attachments/assets/fd615154-ca95-49d3-bdba-62751fc9c079)

- Menggabungkan dataframe ratings dengan `movie_info` Berdasarkan Nilai `movieId

  ![4](https://github.com/user-attachments/assets/4ef808ef-f031-41e7-b28b-ff0a6a2e05c2)

- Menggabungkan data dengan featuers `movies`

  ![5](https://github.com/user-attachments/assets/07c0ab1c-231c-4adb-8a7d-ff9e7c814d0b)

## Data Preparation
Data preparation adalah proses mempersiapkan data mentah menjadi bentuk yang siap digunakan untuk analisis, pemodelan, atau pelatihan algoritma machine learning. Tahapan ini mencakup berbagai langkah untuk memastikan data bersih, konsisten, relevan, dan terstruktur dengan baik.

- Mengatasi missing value : menyeleksi data apakah data tersebut ada yang kosong atau tidak  

  ![missing](https://github.com/user-attachments/assets/cdb1d148-03a1-4e3f-80b6-96a695bff3f6)

- Data Cleaning : proses identifikasi, perbaikan, atau penghapusan data yang tidak lengkap, tidak akurat, tidak konsisten, atau tidak relevan dalam dataset.

  ![cleaning](https://github.com/user-attachments/assets/93d53dc3-0831-416c-94a3-6abf9b6b6cdc)

  ![clening 2](https://github.com/user-attachments/assets/6f8408fe-5da4-4bd9-a32a-d05295b1bdaa)

- Mengurutan data : untuk mengurutkan data berdasarkan movieId secara asceding.

  ![assending](https://github.com/user-attachments/assets/2fd07bca-4e3f-4c8f-8bcc-0dc1cab0fc1a)

- Mengatasi duplikasi data : mengatasi data yang muncul lebih dari satu kali dalam sebuah dataset, baik secara keseluruhan maupun sebagian

  ![duplicates](https://github.com/user-attachments/assets/07dc83e3-01d2-4ced-bc78-dfadfd57e1a3)

- Konversi data menjadi list : untuk mengubah data menjadi list

  ![konversidata](https://github.com/user-attachments/assets/9e83ec7a-7926-4222-a0e9-5f3456d6958a)

- Membuat dictionary : Untuk membuat dictionary dari data yang ada.

  ![dicsionary](https://github.com/user-attachments/assets/8c238a35-25f1-4794-9898-3a7a50fd6bc4)

## Modeling dan Result
Proses pemodelan yang saya lakukan pada data ini mencakup penerapan algoritma machine learning, yaitu `content-based filtering` yang digunakan didasarkan pada preferensi pengguna terhadap item yang telah mereka sukai di masa lalu dan `collaborative filtering` yang digunakan untuk memanfaatkan tingkat rating yang diberikan oleh pengguna terhadap film untuk menghasilkan rekomendasi yang relevan.

1. Menggunakan `content-based filtering`
*Content-Based Filtering* adalah salah satu metode dalam sistem rekomendasi yang digunakan untuk memberikan rekomendasi kepada pengguna berdasarkan karakteristik atau atribut dari item yang telah mereka interaksikan atau sukai sebelumnya. Pada proyek ini, saya akan menggunakan pendekatan content-based filtering untuk mengembangkan model yang bertujuan membangun sistem rekomendasi film sesuai dengan tujuan proyek. Proses pengembangan sistem ini dilakukan melalui beberapa tahapan, yaitu:

   - TFIDFVetorizer()

     Menggunakan TF-IDF (Term Frequency-Inverse Document Frequency) untuk memproses data teks, dalam hal ini, data genre dari film yang ada dalam dataframe movie_new. TfidfVectorizer adalah alat dari pustaka    scikit-learn yang digunakan untuk mengubah teks menjadi representasi numerik berbasis TF-IDF. TF-IDF adalah teknik yang digunakan untuk menilai pentingnya kata dalam dokumen yang bersifat kolektif atau seluruh korpus.

     ![tf 1](https://github.com/user-attachments/assets/568c6172-610c-4568-b595-10f8635363a1)

     Kemudian dapat melakukan fit dan transformasi ke dalam bentuk matirx

     ![tf 2](https://github.com/user-attachments/assets/a87ae4be-e977-4e6b-8e47-5baeebeaba7c)

     Menghasilkan vektor tf-idf dalam bentuk matrix, menggunakan fungsi todense().

     ![tf 3](https://github.com/user-attachments/assets/9c91606a-a5a1-40f3-9277-3b2b5504cf6b)

     Lihat matrix tf-idf untuk beberapa movie (movie_name) dan genre

     ![tf 4](https://github.com/user-attachments/assets/22619f68-6d09-42d1-a2f2-186335aa48e7)


   - Perhitungan *cosine similarity*

     *Cosine Similarity* digunakan untuk menghitung derajat kesamaan (similarity degree) antar film.  *Cosine Similarity* adalah sebuah ukuran yang digunakan untuk menghitung seberapa mirip dua vektor dalam ruang vektor berdimensi tinggi, dengan menggunakan sudut antara kedua vektor tersebut. Meskipun vektor dapat memiliki panjang yang berbeda, Cosine Similarity mengukur kesamaan arah antara dua vektor, bukan panjangnya.

     ![cos 1](https://github.com/user-attachments/assets/891d83ca-4676-4342-8b0f-28145272248b)
  
     Membuat dataframe dari variabel cosine_sim_df dengan baris dan kolom berupa nama movie, serta melihat kesamaan matrix dari setiap movie

     ![cos 2](https://github.com/user-attachments/assets/4e322cf3-bace-41ef-b189-48c60f8827bf)

    - Rekomendasi Testing

      Membuat fungsi movie_recommendations dengan beberapa parameter sebagai berikut:
      - Nama_movie : Nama judul dari movie tersebut (index kemiripan dataframe).
      - Similarity_data : Dataframe mengenai similarity yang telah kita didefinisikan sebelumnya
      - Items : Nama dan fitur yang digunakan untuk mendefinisikan kemiripan, dalam hal ini adalah ‘movie_name’ dan ‘genre’.
      - k : Banyak rekomendasi yang ingin diberikan.
      
      ![recom 1](https://github.com/user-attachments/assets/6b4b0963-c368-44c7-9edd-1bcd74401123)

      Setelah membuat fungsi untuk melakukan rekomendasi film, dapat menerapkan kode di atas untuk menemukan rekomendasi movie yang mirip dengan `Juno (2007)`.

      ![recom 2](https://github.com/user-attachments/assets/921bde32-5af3-4f62-b80a-6a509a5a9e17)

      Berikut ini merupakan Top 5 Recommendations berdasarkan genre dari film `Juno (2007)`. Sistem telah berhasil merekomendasikan film dengan sesuai, bisa dilihat pada hasil yang mendapatkan rekomendasi film yang mirip dengan genre Comedy, Drama, Romance..

      ![recom 3](https://github.com/user-attachments/assets/e97af899-6429-46ce-ad61-9f72184b3938)

  

    Kelebihan Content-Based Filtering

   - Mampu menjelaskan bagaimana hasil rekomendasi didapatkan
     
   - Kemampuan untuk merekomendasikan item yang sifatnya baru bagi pengguna bahkan belum pernah di-rate oleh siapapun, karena prinsip kerjanya yaitu dengan melihat deskripsi item yang terdapat pada item yang pernah diberi nilai rating tinggi

    Kekurangan Content-Based Filtering

   - Terbatasnya rekomendasi hanya pada item-item yang mirip (similar) sehingga tidak ada kesempatan untuk mendapatkan item yang tidak terduga (serendipity)
     
   - Sistem tidak dapat memberikan rekomendasi kepada pengguna baru yang belum pernah melakukan aktivitas apapun dan tidak memiliki profil user yang cukup (Cold Start Problem)


2. Menggunakan `collaborative filtering`

   *Collaborative Filtering* adalah teknik yang digunakan dalam sistem rekomendasi untuk memberikan rekomendasi berdasarkan preferensi atau interaksi pengguna lain. Pendekatan ini tidak bergantung pada atribut atau konten dari item itu sendiri (seperti dalam Content-Based Filtering).

   - Preparation

     Proses encoding dilakukan pada tahap ini, dengan melakukan encode pada feature 'userId' dan 'movieId'. proses encode akan memetakan setiap nilai pada kedua feature tersebut ke dalam bentuk index.
     ![preperetion 1](https://github.com/user-attachments/assets/4d619a26-01ea-466f-8601-36857c94719f)

     ![preperetion 2](https://github.com/user-attachments/assets/2cb839b7-be08-407b-88a9-7dace07497e4)

     Terakhir, periksa beberapa informasi dalam data seperti total pengguna, total film, ubah nilai rating menjadi tipe data float, serta cek nilai minimum dan maksimum.

     ![preperetion 3](https://github.com/user-attachments/assets/2a4ce92a-2bc4-443d-8dbf-ce184a96386f)

   - Split Data for Training and Validation

     Data dibagi untuk data train dan validasi dengan komposisi 80/20. Pembagian ini bertujuan agar data yang digunakan dapat digunakan untuk mengembangkan model dan mengevaluasi performance dari model yang telah dikembangkan.

     ![train 1](https://github.com/user-attachments/assets/6ae5ad3a-b1b8-46a1-8ac1-f6dc5863bb72)

   - RecommenderNet

     ![recommennet](https://github.com/user-attachments/assets/89ac9a2f-dd2f-4c97-9c0a-f921497560f2)


   - Training

     Proses training dilakukan dengan mengimplementasikan teknik embedding untuk menghitung skor kecocokan antara film dengan users. kemudian, pada  proses compile dilakukan menggunakan BinaryCrossentropy untuk menghitung loss function, Adam (Adaptive Moment Estimation) sebagai optimizer, dan root mean squared error (RMSE) sebagai metrics evaluation. Proses training model berjalan sebanyak 100 epochs sebagai berikut.

     ![traing 2](https://github.com/user-attachments/assets/0603faac-876e-4597-8443-be9c2aac5880)

     ![training 3](https://github.com/user-attachments/assets/f4ddcd89-3d73-40c3-b9de-6213979d8a65)


   - Rekomendasi Testing

   




## Evaluation
## Referensi
1. antaranews.com (2020, 10 Oktober). Layanan "streaming", tantangan dan peluang perfilman Indonesia. Diakses pada 25 November 2024, dari https://www.antaranews.com/berita/1776245/layanan-streaming-tantangan-dan-peluang-perfilman-indonesia#google_vignette
2. kumparan.com. (2021, 31 Agustus). Mengenal Istilah Binge Watching dan Hopping yang Jadi Tren Terbaru Nonton Film. Diakses pada 25 November 2024, dari https://kumparan.com/millennial/mengenal-istilah-binge-watching-dan-hopping-yang-jadi-tren-terbaru-nonton-film-1wREvjSoXeB
3. Arfisko, Hilmi Hidayat dan Wibowo, Agung Toto. 2022. “Sistem Rekomendasi Film Menggunakan Metode Hybrid Collaborative Filtering Dan Content-based Filtering”. *e-Proceeding of Engineering*, Vol.9, No. 3 Juni 2022: 2159.
4. Wiputra, Michael M., and Yusup J. Shandi. "Perancangan Sistem Rekomendasi Menggunakan Metode Collaborative Filtering dengan Studi Kasus Perancangan Website Rekomendasi Film". *Media Informatika*, vol. 20, no. 1, 2021, pp. 1-18, doi:[10.37595/mediainfo.v20i1.54](https://dx.doi.org/10.37595/mediainfo.v20i1.54).

