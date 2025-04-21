# Laporan Machine Learning: I Kadek Adi Memes Subagia
---  
# Project Overview

> **Domain Project Yang Dipilih pada project ini adalah mengenai Rekomendasi Buku"System Recomendation Buku"**

<p align = "Justify">Perkembangan industri buku saat ini terus mengalami kemajuan, dengan banyaknya judul dan penulis yang menawarkan cerita menarik, informatif, dan menginspirasi. Penerbit besar maupun independen berlomba-lomba menyajikan karya terbaik mereka, baik dalam bentuk cetak maupun digital. Di era digital sekarang, platform pembelian dan pembacaan buku seperti Goodreads, Amazon, dan Google Books semakin memudahkan kita untuk mengakses ribuan bahkan jutaan judul buku.Namun, dengan begitu banyaknya pilihan buku yang tersedia, pembaca seringkali kebingungan dalam memilih buku yang sesuai dengan selera dan kebutuhannya. Hal ini juga menjadi tantangan tersendiri bagi penulis dan penerbit untuk mengetahui preferensi pembaca dan tren pasar.Oleh karena itu, sistem rekomendasi buku hadir sebagai solusi untuk membantu pembaca menemukan buku yang sesuai dengan minat mereka berdasarkan judul, Author, rating, dan preferensi pengguna lainnya. Sistem ini juga dapat membantu penerbit dan penulis memahami arah selera pasar dalam pengembangan buku selanjutnya.</p> 

![image](https://github.com/user-attachments/assets/b41869e7-e053-4868-93f1-4c14ee861dc9)

<p align = "Justify" >Sistem Rekomendasi adalah salah satu cara untuk menguntungkan kedua belah pihak konsumen yang bisa memilih Buku apa yang sesuai dengan selera mereka, dan Author Buku bisa mempelajari dari data konsumen dengan memanfaatkan perkembangan teknologi sekarang, menggunakan teknologi Machine Learning dapat membuat sistem rekomendasi yang menguntungkan dua belah pihak ini. <a href = "https://ejurnal.umri.ac.id/index.php/coscitech/article/view/5131">[1]</a></p> 

# Business Understanding 
--- 
Dari Latar Belakang di atas kita bisa diambil Problem

### Problem
* Bagaimana cara melakukan pra-pemrosesan pada data Dataset yang akan digunakan agar dapat membuat model yang baik menggunakan teknik content based filtering dan dan collaborative filtering?
* Bagaimana memberikan rekomendasi Buku berdasarkan Data pada setiap judul Buku yang pelanggan input sehingga dapat memberikan preferensi yang sesuai Konsumen inginkan?

### Goals
* Melakukan pra-pemrosesan pada dataset agar nantinya dapat diproses pada model yang menggunaan teknik content based filltering dan collaborative filltering.
* Memberikan referensi judul buku untuk mempermudah pelanggan mencari buku yang sesuai dengan selera mereka dengan model yang sudah dibangun.

### Problem Statment
untuk mencapai Goals yang ada dapat melakukan bebrapa solusi yaitu :
* Untuk tujuan pertama, melakukan pra-pemrosesan data dengan bebrapa teknik yaitu:
  * Memeriksa masalah data yang ada dalam dataset.
  * Melakukan visualisasi data untuk mempelajari data.
  * Membersihkan judul buku yang duplikat dalam dataset
* Untuk tujuan kedua yaitu membuat rekomendasi judul buku kepada pengguna dengan menggunakan dua metode yaitu Content based filltering dan collaborative filltering.
  * Content based filltering.
    <br>adalah metode yang memilih item berdasarkan korelasi antara konten item dan preferensi pengguna <a href = "https://users.ics.forth.gr/~potamias/mlnia/paper_6.pdf">[2]</a>, Content-based filtering
    mempelajari profil minat pengguna baru berdasarkan data dari objek yang telah
    dinilai pengguna. Algoritma ini bekerja dengan menyarankan item serupa yang pernah disukai di masa lalu atau sedang dilihat di masa kini kepada pengguna. Metode ini memiliki kelebihan dan kekurangan
    diantarinya adalah :
    * Kelebihan
      <br>Metode ini tidak bergantung pada pengguna lain karena menggunakan data milik sendiri.
    * Kekurangan
      <br>Tidak cocok untuk new user karena metode ini sangat memerlukan data riwayat dari pengguna.
  * Collaborative filltering
    <br>adalah metode yang bekerja dengan dengan mencari sekelompok besar orang dan menemukan sekelompok kecil pengguna dengan selera yang mirip dengan pengguna tertentu. Ia melihat item yang mereka sukai dan
    menggabungkannya untuk membuat daftar saran yang diberi peringkat. Metode ini juga memiliki kelebihan dan kekurangan yaitu :
    * Kelebihan
      <br>Metode ini tidak bergantung pada informasi item secara eksplisit karena mengandalkan pola interaksi antar pengguna.
    * Kekurangan
      <br>Tidak cocok untuk pengguna baru karena metode ini sangat memerlukan riwayat interaksi untuk menghasilkan rekomendasi.

# Data Understanding
--- 
Dalam Project ini menggunakan dataset yang sudah tersedia dalam situs Kaggle, dimana data ini memiliki 3 buah data inti yaitu data buku, rating, user pada data ini terdapat fitur yang bisa digunakan untuk membuat sebuah sistem rekomendasi yang bisa memberikan referensi buku yang sesuai dengan pendekatan dari pengguna. <br>
Referensi [Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset/data) <br>
![image](https://github.com/user-attachments/assets/78c5ac7e-629c-4d65-8531-74fc54c7956e)

Pada Data ini terdapat 3 file csv <br>
*   Books.csv <br>
Berisikan Data dari Buku yang ada mulai dari Judul, Author, Publiser, tahun rilis dan yang lainnya yang berkaitan dengan Buku
*   Ratings.csv <br>
Berisikan Data Penilaian pada Buku dari User yang membacanya
*  User.csv <br>
Berisikan data dari pembaca / User mulai dari umur sampai tempat tinggal mereka <br>

![image](https://github.com/user-attachments/assets/bf2a2db6-81d3-409b-9a90-1353737f0957) <br>

### Books CSV
Pada data Books.csv terdapat 8 kolom data yang berisikan 271360 baris data.<br>
- ISBN Merupakan kode unik identifikasi buku (International Standard Book Number).
- Book-Title Data Judul Buku yang ada
- Book-Author Data Penulis Buku
- Year-Of-Publication Data Tahun Buku itu diterbitkan
- Publisher Data Para Publisher Buku
- Image-URL-S Data URL gambar kecil dari sampul buku.
- Iamage-URL-M Data URL gambar sedang dari sampul buku.
- Image-URL-L Data URL gambar besar dari sampul buku.

![image](https://github.com/user-attachments/assets/1b89d1f6-33ee-460a-b7aa-773fb402129d)

### Rating CSV
Pada data Rating.csv terdapat 3 kolom data yang berisikan 1149780 baris data <br>
- User-Id adalah Data ID dari User
- ISBN adalah kode unik dari buku (International Standar Book Number)
- Book Rating Data Rating dari user untuk Buku yang dibaca

![image](https://github.com/user-attachments/assets/fe107921-59a5-4669-b7e0-2daab5967134)

### User CSV
Pada data User.csv terdapat 3 kolom data yang berisikan 278858  baris data <br>
- User-Id adalah Data ID dari User
- Location adalah yang berisikan location dari User
- Age adalah data yang berisikan info umur dari User

![image](https://github.com/user-attachments/assets/558dd8e5-f410-41b8-ba0c-1c7f5c88c1e9) <br>

Kemudian pada tahap ini dilakukan pengecekan data, apakah ada data yang mengalami missing value ? data yang mengalami duplikat, dan melakukan visualisasi data untuk lebih jelas dalam memahami data yang ada <br>

pada pengecekan data yang mengalami missing value terdapat beberapa colom yang mengalami missing value <br>
![image](https://github.com/user-attachments/assets/c30830a5-2543-4135-888d-ba5f8f1b753c) <br>
Dilihat ada dua dataset yang memiliki data missing pada colomnya yaitu data pada Books yaitu colom : ```'Book-Author', 'Publisher', 'Image-URL-L'``` Untuk kasus ini bisa membuang data yang ada, dikarenakan jumlah data yang missing hanya sedikit dan tidak terlalu mempengaruhi model nantinya <br>
Untuk data lagi satu yaitu data Users pada colom : ```Age``` Untuk kasus ini kita tidak bisa menggunakan metode yang sama pada data missing dalam data Books, karena jumlah data yang missing disini terlalu banyak dan sangat beresiko jika kita hapus semua data yang missing tersebut, dikarenakan itu menggunakan metode median, dimana menggati data yang missing tersebut dengan nilai rata-rata dari data ```Age``` <br>
langkah-langkah tersebut akan dilakukan pada tahap Data Preparation.

### Visualisasi Data
Pada Tahap ini melakukan tiga visualisasi data yaitu :
* Melihat Author Terbanyak dan Top Publisher
* Melihat Trend Tahun Distribusi Buku
* Melihat Jumlah Rating Buku

#### Melihat Author Terbanyak dan Top Publisher
Untuk melihat jumlah Author dan publisher bisa menggunakan bantuan libary pandas dengan code ```value_count()``` untuk menghitung keseluruhan jumlah dari data author dan publisher<br>
kemudian dalam membuat chart dibantu dengan libary seaborn<br>
![image](https://github.com/user-attachments/assets/8ba49f71-acf3-453e-98a6-1bff7f660a6c) <br>
pada grafik Dilihat Bahwa Untuk Author Terbanyak yaitu ada Agatha Christie sebanyak lebih dari 600 buku yang ada dan kemudian di bagian publisher yaitu ada Harlequin yang menjadi top publisher dengan lebih dari 7000 buku <br>

#### Melihat Trend Tahun Distribusi Buku
Disini sama dari sebelumnya kita menggunakan bantuan libary seaborn untuk membuat chart tabelnya namun karena pada data Year-of-publication terdapat sedikit kesalahan type data dan terdapat data yang bernilai 0 pada data dikarenakan itu pada grafik menampilkan data yang kurang akurat
![image](https://github.com/user-attachments/assets/fb67d2be-c22e-47d4-983c-e64130647a08) <br>

#### Melihat Jumlah Rating Buku
Pada tahap ini juga sama menggunakan libary seaborn untuk membuat chartnya, dan dilihat dari data user banyak memberikan rating 0 pada buku dan yang paling sedikit adalah rating 1
![image](https://github.com/user-attachments/assets/19b97ab4-7e4e-4461-a6c3-b59af4e651da)


# Data Preparation
Pada Tahapan ini ada beberapa yang perlu dilakukan untuk selanjutnya membuat Model Yaitu:
* Memperbaiki type data pada colom Year-Of-Publication dan Age
* Memperbaiki data yang memiliki missing value
* Menghapus data nan pada Year-of-publication
* Menggabung Dataset Books dan Ratings untuk Mencari top Buku

### Memperbaiki type data pada colom Year-Of-Publication dan Age
![image](https://github.com/user-attachments/assets/c4bf14e7-de35-4e9e-9598-7cdce1dce6b8) <br>
Disini pada colom Year-Of-Publication dan Age mengganti type data yang awalnya type object menjadi int<br>
dengan memanfaatkan libary pandas dengan kode ```astype('Int64')```

### Memperbaiki data yang memiliki missing value
#### Colom 'Book-Author', 'Publisher', 'Image-URL-L'
![image](https://github.com/user-attachments/assets/c30830a5-2543-4135-888d-ba5f8f1b753c) <br>
Pada tahapan ini kita membuat dua metode yaitu dengan menggunakan ```dropna()``` Pada colom ```'Book-Author', 'Publisher', 'Image-URL-L'``` <br>
#### Colom 'Age'
![image](https://github.com/user-attachments/assets/ed0a9efd-bd3e-4d6d-8bbf-ae52b0d9e7ac) <br>
Sedangkan pada colom Age di data Users kita menggunakan metode Mengganti nilai yang missing value dengan ```.median()``` dari nilai colom Age 

### Menghapus data nan pada Year-of-Publication 
Tapah ini yaitu menggunakan libary pandas dalam mengatasi data yang nan, dan mengatur untuk hanya mengambil data dengan rentang tahun 1900 sampai 2025 <br>
```Books = Books[Books['Year-Of-Publication'].notna()]``` <br>
```Books = Books[(Books['Year-Of-Publication'] >= 1900) & (Books['Year-Of-Publication'] <= 2025)]``` <br>
dan dengan data yang baru bisa untuk melihat trend dari publikasi buku tahunan. <br>
![image](https://github.com/user-attachments/assets/87808ef5-6572-45c1-acf7-a50688f938bc) <br>

### Menggabung Dataset Books dan Ratings untuk Mencai top Buku
Tahap ini memiliki beberapa tahapan :
* Menggabungkan data Books dan Ratings melalui colom ```ISBN``` dengan bantuan libary pandas yaitu ```merge()```
* kemudian membuat feature untuk jumlah rating dan rata-rata rating
* Setelahnya membuat feature populer dengan mengambil buku yang hanya di rating lebih dari 300 dan memiliki rata-rata 10 besar.
* Kemudian membuat dataframe populer_buku dengan menambahkan colom ```'Book-Title','Book-Author','Image-URL-M','num_ratings','avg_rating'```
![image](https://github.com/user-attachments/assets/24d01605-552c-4c68-9fe2-9ecfeb1669ed)

# Modeling and Result
Pada proyek ini menggunakan dua metode yaitu :
*   Collaborative Filtering
*   content based filltering

## Collaborative Filltering
