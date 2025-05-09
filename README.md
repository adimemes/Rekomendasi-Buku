# Laporan Machine Learning: I Kadek Adi Memes Subagia
---  
# Project Overview

> **Domain Project Yang Dipilih pada project ini adalah mengenai Rekomendasi Buku"System Recomendation Buku"**

<p align = "Justify">Perkembangan industri buku saat ini terus mengalami kemajuan, dengan banyaknya judul dan penulis yang menawarkan cerita menarik, informatif, dan menginspirasi. Penerbit besar maupun independen berlomba-lomba menyajikan karya terbaik mereka, baik dalam bentuk cetak maupun digital. Di era digital sekarang, platform pembelian dan pembacaan buku seperti Goodreads, Amazon, dan Google Books semakin memudahkan kita untuk mengakses ribuan bahkan jutaan judul buku.Namun, dengan begitu banyaknya pilihan buku yang tersedia, pembaca seringkali kebingungan dalam memilih buku yang sesuai dengan selera dan kebutuhannya. Hal ini juga menjadi tantangan tersendiri bagi penulis dan penerbit untuk mengetahui preferensi pembaca dan tren pasar.Oleh karena itu, sistem rekomendasi buku hadir sebagai solusi untuk membantu pembaca menemukan buku yang sesuai dengan minat mereka berdasarkan judul, Author, rating, dan preferensi pengguna lainnya. Sistem ini juga dapat membantu penerbit dan penulis memahami arah selera pasar dalam pengembangan buku selanjutnya.</p> 

![image](https://github.com/user-attachments/assets/b41869e7-e053-4868-93f1-4c14ee861dc9)

<p align = "Justify" >Sistem Rekomendasi adalah salah satu cara untuk menguntungkan kedua belah pihak konsumen yang bisa memilih Buku apa yang sesuai dengan selera mereka, dan Author Buku bisa mempelajari dari data konsumen dengan memanfaatkan perkembangan teknologi sekarang, menggunakan teknologi Machine Learning dapat membuat sistem rekomendasi yang menguntungkan dua belah pihak ini. <a href = "https://ejurnal.umri.ac.id/index.php/coscitech/article/view/5131">[1]</a></p> 

# Business Understanding 
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
### Memperbaiki type data
Pada dataset Books dan User colom ```Year-Of-Publication``` pada bagian Books dan colom ```Age``` pada bagian User. <br>
untuk kasus pada dataset Books colom ```Year-Of-Publication``` yang awalnya data bertipe ```object``` dimana ini salah yang seharusnya data itu memiliki tipe ```int``` dengan code ```Books['Year-Of-Publication'] = Books['Year-Of-Publication'].astype('Int64')``` <br>
dan untuk dataset User colom ```Age``` yang awalnya bertipe ```float``` dimana ini juga salah dan harusnya bertipe ```int``` dengan code ```Users['Age'] = Users['Age'].astype('Int64')``` <br>
Hasil dari perubahan tipe bisa dilihat pada gambar ini. <br>
![image](https://github.com/user-attachments/assets/d2202bd3-7d1f-462a-8ba6-ee1fd5898864) 
<br>
![image](https://github.com/user-attachments/assets/b7d90ae5-8103-4eaa-9f57-dc89d659e8f8)


Pada Tahapan Data Preparation ada beberapa tahapan yang dilakukan:
### Memperbaiki Missing Value
Pada tahapan ini ada dua data yang memiliki nilai missing value yaitu data Books dan Age <br>
* pada bagian books karena nilai missing valuenya sedikit dan tidak terlalu mempengaruhi kondisi model nantinya, bisa menggunakan perintah ```.dropna()``` yang berfungsi untuk membuang data yang memiliki kondisi missing value.
* kemudian pada tahapan age karena data yang missing terlalu banyak dan berpengaruh pada tahapan modeling, karena itu bisa menggunakan nilai median untuk nilai yang mengalami missing value dengan code ```Users['Age'] = Users['Age'].fillna(Users['Age'].median())```
### Memperbaiki outlier pada colom Year-of-publication
pada tahapan ini bertujuan untuk memperbaiki nilai data yang ada pada colom ```Year-of-publication``` karena pada data ada data yang janggal dimulai dari data yang bernilai ```NaN``` data tahun 0 dan data tahun yang melewati 2025, untuk mengatasi hal ini menggunakan cara yaitu menghapus nilai ```NaN``` dengan fungsi ```.dropna()``` kemudian menghapus semua data yang tidak termasuk pada data bernilai 1900 sampai 2025 dengan code ```Books = Books[(Books['Year-Of-Publication'] >= 1900) & (Books['Year-Of-Publication'] <= 2025)]``` kemudian kembali membuat grafik untuk memeriksa grafik ```Year-of-publication``` dengan data yang lebih bersih. <br>
![image](https://github.com/user-attachments/assets/7d4a802f-dd80-40b8-80e6-98ef52efbce1)

### Menggabung Dataset Books dan Ratings untuk Mencai top Buku
Tahap ini memiliki beberapa tahapan :
* Menggabungkan data Books dan Ratings melalui colom ```ISBN``` dengan bantuan libary pandas yaitu ```merge()```
* kemudian membuat feature untuk jumlah rating dan rata-rata rating
* Setelahnya membuat feature populer dengan mengambil buku yang hanya di rating lebih dari 300 dan memiliki rata-rata 50 besar.
* Kemudian membuat dataframe populer_buku dengan menambahkan colom ```'Book-Title','Book-Author','Image-URL-M','num_ratings','avg_rating'```
![image](https://github.com/user-attachments/assets/24d01605-552c-4c68-9fe2-9ecfeb1669ed)

### Collaborative Filtering
* Split data <br>
Pada tahapan data preparation dalam model Collaborative Filltering di proyek ini membagi data penting yaitu pada bagian ```user_rating_counts``` hanya mengambil data ```Book-Rating``` yang telah memberikan rating pada lebih dari 200 buku dengan code ```user_rating_counts = rating_buku.groupby('User-ID').count()['Book-Rating'] > 200
```. kemudian di simpan pada ```good_reader``` dan menghitung jumlah berapa user yang memberikan rating. dengan code ```good_reader = user_rating_counts[user_rating_counts].index``` <br>
kemudian tahapan selanjutnya adalah membagi data top buku yang sudah diberi rating sebanyak lebih dari 50 kali dan menyimpan pada ```final_ratings ``` dengan code ```y = filtered_rating.groupby('Book-Title').count()['Book-Rating']>=50 famous_books = y[y].index``` dan terakhir di filter kembali pada ```final_ratings``` dengan code ```final_ratings = filtered_rating[filtered_rating['Book-Title'].isin(famous_books)]```<br>
* Pivot table <br>
pada tahapan ini adalah membuat pivot table yang berguna untuk mengubah data rating yang awalnya berbentuk long format menjadi format matriks untuk memudahkan dalam menghitung cosine similarity antar buku <br>
proses pembuatan pivot table yaitu dengan memanfaatkan data ```User-ID```. ```Book-Title```, dan ```Book-Rating``` dengan code seperti berikut : <br>
```pt = final_ratings.pivot_table(index='Book-Title',columns='User-ID',values='Book-Rating')``` kemudian mengatisipasi nilai ```NaN``` pada pivot table dengan mengganti nilai yang ```NaN``` dengan 0 dengan cara
```pt.fillna(0,inplace=True)``` <br>
![image](https://github.com/user-attachments/assets/d1982ae5-3649-41ff-b059-7762b0ccf686)

### Content based filltering
* TF-IDF <br>
pada tahapan ini berfungsi untuk membuat Tokenisasi nama penulis yang berfungsi untuk menghitung frekuensi jumlah nama penulis yang sering muncul dari tahap Tokenisasi yang disebut TF, kemudian untuk nama penulis yang jarang keluar akan memiliki bobot tersendiri yaitu IDF. <br>
kemudian TF-IDF melakukan perhitungan dengan cara TF x IDF, Ini memberikan bobot lebih tinggi pada bagian nama yang unik dan membedakan satu penulis dari yang lain. <br>
Contoh: "Tolkien" akan memiliki nilai TF-IDF lebih tinggi daripada "John" karena lebih unik.<br>

untuk melakukan TF-IDF menggunakan code seperti ini: <br>
```vectorizer = TfidfVectorizer()``` ```author_matrix = vectorizer.fit_transform(author_df['Book-Author'])``` <br>
untuk kode ```vectorizer = TfidfVectorizer()``` memiliki fungsi untuk membuat Tokensasi, kemudian pada code ```author_matrix = vectorizer.fit_transform(author_df['Book-Author'])``` berfungsi untuk membuat Tokensasi pada nama author.

# Modeling and Result
Pada proyek ini menggunakan dua metode yaitu :
*   Collaborative Filtering
*   content based filltering

## Collaborative Filltering
Collaborative filtering adalah algoritma sistem rekomendasi yang bergantung pada pendapat komunitas pengguna. tidak memerlukan atribut untuk setiap itemnya seperti pada sistem berbasis konten. Collaborative filtering dibagi lagi menjadi dua kategori, yaitu: model based (metode berbasis model machine learning) dan memory based (metode berbasis memori). cara kerja algoritma ini bisa diasumsikan seperti ini yaitu jika pengguna A memiliki opini yang sama dengan pengguna B tentang suatu item, maka pengguna A lebih cenderung memiliki opini pengguna B untuk item lain daripada opini pengguna yang dipilih secara acak. dengan intinya algoritma ini memiliki konsep ```"Pengguna yang menyukai item yang sama dengan Anda juga menyukai item-item ini."``` <br>
pada proyek ini juga memiliki konsep yang sama dimana akan memberikan rekomendasi berdasarkan rating yang diberikan oleh user pada top buku, dengan menginput judul buku kemudian akan memberikan Top 5 buku yang user lain sukai. <br>
![image](https://github.com/user-attachments/assets/fecb9b98-0382-43a1-9ad0-92d6b9b75041)

## Content Based Filltering
Content-Based Filtering adalah teknik sistem rekomendasi yang merekomendasikan item berdasarkan deskripsi item dan profil preferensi pengguna. Algoritma ini bekerja dengan menyarankan item serupa yang pernah disukai di masa lalu atau sedang dilihat di masa kini kepada pengguna. Semakin banyak informasi yang diberikan pengguna, semakin baik akurasi sistem rekomendasi. <br>
intinya algoritma ini adalah ```"Anda menyukai item dengan karakteristik ini, jadi Anda mungkin juga menyukai item lain dengan karakteristik serupa."```<br>
pada proyek ini juga memiliki konsep yang sama dimana akan merekomendasikan sesuatu tulisan yang cukup mirip dengan author kesukaan dengan input nama author dan akan memberikan top 5 author. <br>
![image](https://github.com/user-attachments/assets/440e27dc-8e1b-47d2-ab97-5426ae1aaf56)
<br>

pada dua model ini juga menggunakan Cosine Similarty yang merupakan metrik untuk mengukur kemiripan antara dua vektor berdasarkan sudut.
* 1 → dua vektor sangat mirip (arahnya sama)
* 0 → dua vektor tidak ada hubungannya (saling tegak lurus)
* -1 → dua vektor berlawanan arah (jarang terjadi dalam sistem rekomendasi)

adapun rumus perhitungan dari cosine similarty yaitu sebagai berikut. <br>
![image](https://github.com/user-attachments/assets/72e0f00a-89e6-48a2-bbdf-65644e8b4126)
<br>
## Cosine Similarty pada Collaborative Filltering
pada Collaborative filltering penggunaan cosine similarty ```train_similarity = cosine_similarity(pt)``` dimana disini digunakan untuk menghitung kemiripan antar buku berdasarkan kolom pengguna dengan memanfaatkan pivot table sebagai bentuk matriks pengguna dan buku <br>

## Cosine Similarty pada Content Based Filltering
pada Content Based Filltering penggunaan cosine simalrty ```similarities = cosine_similarity(author_vec, author_matrix)[0]```  dimana disini digunakan untuk menghitung kemiripan penulis yang mirip dari vektor fitur tokenisasi  dari TF-IDF <br>

# EVALUASI
## Content Based Filtering
pada evaluasi model Content Based Filtering disini harus membuat sebuah ground data, untuk membuat data penulis dan buku yang disukai oleh USer sebagai Based User <br>
Kemudian adalah pembuatan matrik evaluasi, dimana disini menggunakan: 
* Precision
* recalls
dengan jumlah yang dievaluasi disini adalah 5 <br>
![image](https://github.com/user-attachments/assets/5c3282ed-71f7-4cd0-9785-1be26c9777ad)
<br>Dari Hasil yang didapatkan model masih terbilang kurang dari segi akurasi <br>
dari hasil 5 rekomendasi yang diberikan hasil yang di dapatkan:
* Precision : 4,62%
* Recall : 0,66%
* F1-score : 1,15 %
hal ini didapatkan mungkin karena kurangnya data pada user karena pada dataset user hanya ada colom ID, location dan age yang masih dibilang kurang, karena Content Based Filtering adalah algoritma berdasarkan riwayat User.
<br>

## Collaborative Filtering
Pada Evaluasi untuk model Collaborative Filtering yaitu menggunakan menggunakan RMSE dan menampilkan contoh User dalam memberi rating <br>
![image](https://github.com/user-attachments/assets/11ba2412-b335-4bbe-b322-b9591f19d7a6)
<br>
Dilihat dari hasil yang didapatkan, pada model ini lebih tinggi dibandingkan Contend Based Filltering dimana pada evaluasi matriks mendapatkan nilai: <br>
* RMSE (Root Mean Squared Error) :  7.0683
* MAE (Mean Absolute Error) : 6.3886
* Normalized RMSE = 0.7068
* Akurasi (1 - NRMSE) : 29.32%
dengan akurasi 29,32% masih terbilang cukup rendah, hal ini mungkin bisa dikarenakan jumlah buku masih kurang, dan banyak data buku yang belum diberi rating
<br>

## Perbandingan Model
Dilihat dari hasil Evaluasi, untuk Model Collaborative Filtering masih lebih baik dibanding Contend Based Filtering, hal ini bisa terjadi karena kurangnya data yang dibutuhkan dalam pembuatan model, jika data yang ada lebih banyak bukan tidak mungkin akurasi akan meningkat lebih baik dalam pemberian rekomendasi

<br>

## Apakah Sudah Menjawab Problem Statment :

* Bagaimana cara melakukan pra-pemrosesan pada data Dataset yang akan digunakan agar dapat membuat model yang baik menggunakan teknik content based filtering dan dan collaborative filtering?<br>
Untuk Menjawab Problem Statment ini sudah dijawab pada procesing Data, dimana data dibersihkan mulai dari type data yang tidak cocok, data yang memiliki banyak sekali missing value, data yang terdapat data Nan dan 0 contohnya pada data colom "Year-Of-Publication" yang mengakibatkan grafik awal sebelum procesing data terlihat buruk dan sudah lebih baik pada selesai processing data, dan ditahap procesing data juga sudah menggabungkan dataset books dan ratings untuk nantinya dipakai dalam model
* Bagaimana memberikan rekomendasi Buku berdasarkan Data pada setiap judul Buku yang pelanggan input sehingga dapat memberikan preferensi yang sesuai Konsumen inginkan?
Untuk Pertanyaan ini sudah dijawab dari hasil model yang dibuat, untuk metode Collaborative Filltering sudah mendapatkan rekomendasi buku berdasarkan rating. kemudian pada metode kedua adalah mendapatkan rekomendasi author berdasarkan author kesukaan untuk mencari author yang memiliki cara dan taste yang sama.

## Apakah berhasil mencapai setiap goals yang diharapkan? :
* Melakukan pra-pemrosesan pada dataset agar nantinya dapat diproses pada model yang menggunaan teknik content based filltering dan collaborative filltering.<br>
Goals ini sudah terjawab pada tahap Processing data, dimana sudah berhasil untuk memperbaiki type data, missing value, kesalahan value dan menggabungkan dataset untuk membuat model.
* Memberikan referensi judul buku untuk mempermudah pelanggan mencari buku yang sesuai dengan selera mereka dengan model yang sudah dibangun. <br>
Goals ini berhasil dengan berjalannya metode collaborative filltering dan memberikan rekomendasi buku

## Apakah setiap solusi statement yang kamu rencanakan berdampak? :
* Untuk Problrem Statment Pertama Melakukan pra-pemrosesan data:
Tahap ini sudah Berdampak pada tahap praprocesing data dengan tidak adanya type data yang salah, missing value dan feature baru yang berisikan data yang sudah siap untuk permodelan.<br>

* Untuk Problem Statment Kedua yaitu melakukan metode Collaborative Filltering dan Content Based Flltering: Tahap ini juga sudah berhasil dengan output rekomendasi buku dan author yang diberikan dari kedua metode tersebut

# REFERNSI
[1] R. Ardiansyah, B. D. Saputra, and M. A. Bianto, "Sistem rekomendasi buku perpustakaan sekolah menggunakan metode content-based filtering," *Jurnal Computer Science and Information Technology (CoSciTech)*, vol. 4, no. 2, pp. 510–517, Aug. 2023. doi: [10.37859/coscitech.v4i2.5131](https://doi.org/10.37859/coscitech.v4i2.5131).

[2] R. van Meteren and M. van Someren, "Using content-based filtering for recommendation," NetlinQ Group and University of Amsterdam. [Online]. Available: https://users.ics.forth.gr/~potamias/mlnia/paper_6.pdf

