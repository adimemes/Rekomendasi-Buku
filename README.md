# Laporan Machine Learning: I Kadek Adi Memes Subagia
---  
# Project Overview

> **Domain Project Yang Dipilih pada project ini adalah mengenai Rekomendasi Buku"System Recomendation Buku"**

<p align = "Justify">Perkembangan industri buku saat ini terus mengalami kemajuan, dengan banyaknya genre dan penulis yang menawarkan cerita menarik, informatif, dan menginspirasi. Penerbit besar maupun independen berlomba-lomba menyajikan karya terbaik mereka, baik dalam bentuk cetak maupun digital. Di era digital sekarang, platform pembelian dan pembacaan buku seperti Goodreads, Amazon, dan Google Books semakin memudahkan kita untuk mengakses ribuan bahkan jutaan judul buku.Namun, dengan begitu banyaknya pilihan buku yang tersedia, pembaca seringkali kebingungan dalam memilih buku yang sesuai dengan selera dan kebutuhannya. Hal ini juga menjadi tantangan tersendiri bagi penulis dan penerbit untuk mengetahui preferensi pembaca dan tren pasar.Oleh karena itu, sistem rekomendasi buku hadir sebagai solusi untuk membantu pembaca menemukan buku yang sesuai dengan minat mereka berdasarkan genre, rating, dan preferensi pengguna lainnya. Sistem ini juga dapat membantu penerbit dan penulis memahami arah selera pasar dalam pengembangan buku selanjutnya.</p> 

![image](https://github.com/user-attachments/assets/b41869e7-e053-4868-93f1-4c14ee861dc9)

<p align = "Justify" >Sistem Rekomendasi adalah salah satu cara untuk menguntungkan kedua belah pihak konsumen yang bisa memilih Buku apa yang sesuai dengan selera mereka, dan Author Buku bisa mempelajari dari data konsumen dengan memanfaatkan perkembangan teknologi sekarang, menggunakan teknologi Machine Learning dapat membuat sistem rekomendasi yang menguntungkan dua belah pihak ini. <a href = "https://ejurnal.umri.ac.id/index.php/coscitech/article/view/5131">[1]</a></p> 

# Business Understanding 
--- 
Dari Latar Belakang di atas kita bisa diambil Problem

### Problem
* Bagaimana cara melakukan pra-pemrosesan pada data list buku yang akan digunakan agar dapat membuat model yang baik menggunakan teknik content based filtering dan dan collaborative filtering?
* Bagaimana memberikan rekomendasi Buku berdasarkan genre pada setiap judul Buku yang pelanggan input sehingga dapat memberikan preferensi yang sesuai Konsumen inginkan?

### Goals
* Melakukan pra-pemrosesan pada data list buku agar nantinya dapat diproses pada model yang menggunaan teknik content based filltering dan collaborative filltering.
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
Dalam Project ini menggunakan dataset yang sudah tersedia dalam situs Kaggle, dimana data ini memiliki 3 buah data inti yaitu data buku, rating, user pada data ini terdapat fitur yang bisa digunakan untuk membuat sebuah sistem rekomendasi yang bisa memberikan referensi buku yang sesuai dengan genre dari pengguna. <br>
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

Pada data Books.csv terdapat 8 kolom data yang berisikan 271360 baris data.<br>
- ISBN Merupakan kode unik identifikasi buku (International Standard Book Number).
- Book-Title Data Judul Buku yang ada
- Book-Author Data Penulis Buku
- Year-Of-Publication Data Tahun Buku itu diterbitkan
- Publisher Data Para Publisher Buku
- Image-URL-S Data URL gambar kecil dari sampul buku.
- Iamage-URL-M Data URL gambar sedang dari sampul buku.
- Image-URL-L Data URL gambar besar dari sampul buku.
<br>
![image](https://github.com/user-attachments/assets/b18b06e7-4642-47c0-a957-a4a6801fdabc)
