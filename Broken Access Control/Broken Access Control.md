## Broken Access Control

### Informasi Dasar
### Deskripsi : 
Broken Access Control adalah sebuah kelemahan keamanan pada aplikasi ketika mekanisme kontrol akses (authorization) tidak diterapkan, tidak konsisten, atau dapat dengan mudah dilewati. Kontrol akses adalah proses yang menentukan apa saja yang boleh dilakukan oleh pengguna setelah mereka berhasil terautentikasi. Ketika kontrol ini rusak atau salah diterapkan, pengguna dapat melakukan tindakan di luar haknya, seperti membaca data pengguna lain, memodifikasi informasi sensitif, menghapus data penting, atau mengakses fitur administratif.

Pada aplikasi modern, kontrol akses menjadi bagian yang sangat penting karena setiap pengguna idealnya memiliki batasan tertentu berdasarkan perannya (role-based), identitasnya (user-based), atau atribut lainnya (attribute-based). Broken Access Control terjadi ketika batasan ini tidak dijaga dengan benar oleh server, sehingga aplikasi tidak mampu menegakkan aturan yang seharusnya membatasi ruang gerak pengguna.

Masalah ini dapat muncul di berbagai titik, seperti endpoint API yang tidak memeriksa hak akses, URL yang dapat dimanipulasi, form yang tidak divalidasi, hingga konfigurasi server yang salah. Kesalahan ini sering berbahaya karena sifatnya yang tidak terlihat—aplikasi tampak berjalan normal, namun di balik itu penyerang dapat memanfaatkan celah untuk mengakses area yang seharusnya dilindungi.

### Target Serangan : 
Semua jenis Web Server, application server, dan web application rentan dan mudah untuk terkena beberapa permasalahan ini. Bahkan website yang hanya bersifat statis, jika tidak diatur dengan baik, dapat diretas oleh hacker, seperti akses terhadap file - file penting, deface, ataupun beberapa perbuatan merusak lainnya. 

### Bagaimana cara mengetahui keamanan Access Control : 
Semua website dipastikan membutuhkan access control. Oleh karena itu aturan dan desain nya sendiri harus secara jelas dan terdokumentasi. Jika tidak ada dokumentasi hampir dipastikan, website tersebut kemungkinan besar rentan. Code yang digunakan harus terstruktur, modular, dan sebagian besar terpusat. Review secara mendetail terhadap code harus dilakukan untuk memvalidasi keabsahan dari implementasi Access Control. Selain itu melakukan test dengan cara membobol code yang digunakan juga akan sangat membantu mengetahui ada atau tidaknya permasalahan pada Access Control.

## Percobaan : Mengubah Isi Keranjang User

1. Setelah melakukan pengaksesan localhost 3000 di terminal dan mempersiapkan aplikasi burpsuite di sini, saya melakukan login dengan menggunakan akun yang sudah di daftarkan sebelumnya.           

[<img src="gambar/gmb1.png" width="800">]

2. Kemudian setelah melakukan proses login disini akan di arahkan ke halaman dashboard untuk dapat memilih beberapa item dan nantinya akan disimpan ke keranjang.

 ![](Gambar/gmb2.png)
 
3. Kemudian menuju halaman keranjang untuk dapat melihat yang telah ditambahkan yaitu carrot juice dan Eggfruit Juice masing masing 1 buah.

 ![](Gambar/gmb3.png)

4. Kemudian disini saya membuka halaman proxy di dalam http history untuk melihat track http history. Terdapat informasi host, method, url, status, length dan informasi pendukung lainnya.

 ![](Gambar/gmb4.png)

5. Kemudian setelah itu saya pilih http history yang memiliki params
 json dengan get /rest/basket/6. Kemudian saya lihat mengenai request
 dan response yang tertampil di halaman tersebut. Dimana response
 berisi informasi isi keranjang yang telah saya pilih sebelumnya.

 ![](Gambar/gmb5.png)

6. Kemudian saya pindahkan list request yang saya amati sebelumnya menuju repeater, kemudian saya send dan pada response terlihat data keranjang yang sudah sesuai dengan apa yang diinputkan sebelumnya.

 ![](Gambar/gmb6.png)

 ![](Gambar/gmb66.png)

7. Setelah melihat informasi response di repeater, saya mencoba untu mengganti data id 6 menjadi 2 untuk melihat apakah terdapat perubahan yang ditampilkan response. Dan ternyata response membrikan informasi berbeda dari sebelumnya yang mana ternyata menunjukkan isi keranjang id 2.

 ![](Gambar/gmb7.png)

8. Kemudian disini saya akan menggunakan fitur interceot untuk menampilkan data keranjang user lain di dalam website owasp juice shop. Dimana saya merubah status intercept yang tadinya off menjadi on.

 ![](Gambar/gmb8.png)

9. Ketika intercept on disini terdapat baris informasi request terkait owasp juice shop. Kemudian saya foorward data tersebut hingga menemukan data get /rest/basket/6, kemudian saya ganti data uiidnya dengan id lain selain id 6 kemudian saya forward kembali informasi tersebut.

 ![](Gambar/gmb9.png)

10. Website berhasil menampilkan isi keranjang pengguna lainnya berikut adalah isi keranjang pengguna : id (2).

 ![](Gambar/gmb10.png)

 ![](Gambar/gmb100.png)

11. Website berhasil menampilkan isi keranjang pengguna lainnya berikut adalah isi keranjang pengguna : id (4).

 [](Gambar/gambar12atas.png)

 ![](Gambar/gambar12bawah.png)

12. Website berhasil menampilkan isi keranjang pengguna lainnya berikut adalah isi keranjang pengguna : id (5).

 ![](Gambar/gambar13atas.png)

 ![](Gambar/gambar13bawah.png)

13. Disini saya sudah berhasil untuk melakukan challenge melihat keranjang orang lain.

 ![](Gambar/gambar14.png)

## Percobaan : Login Admin

1. Disini saya bermaksud ingin mencari data email, yang mana ditemukan di komentar ulasan. Dimana ada informasi email admin disana.

 ![](Gambar/gambar18.png)

2. Kemudian saya melakukan login dengan menggunakan password dummy, namun sebelumnya saya melakukan perubahan status menjadi on di intercept.

 ![](Gambar/gambar19.png)

3. Ketika melakukan submit login, intercept memberikan informasi berupa baris informasi yang mana memuat email dan password.

4. Kemudian setelah melihat informasi tersebut, saya menggunakan ikon yang dikotaki warna merah untuk melakukan pengiriman menuju intruder, positions.

 ![](Gambar/gambar20.png)

5. Kemudian kita berpindah ke halaman intruder, positions dan melihat data informasi yang ada disana, kemudian klik clear. Ada penambahan beberapa data ketika proses melakukan clear data.

 ![](Gambar/gambar21.png)

6. Kemudian klik add, yang mana dalam hal ini akan membuat data email memiliki tambahan sign dollar didepannya. Hal ini membuat adanya perubahan yang ada.

 ![](Gambar/gambar22.png)

7. Proses berikutnya saya menuju ke payloads dan melakukan load data file password.txt yang sebelumnya sudah dibuat.

 ![](Gambar/gambar23.png)

8. Setelah itu kemudian data yang telah digunakan dapat diinputkan pada text akan muncul di dalam kotak putih sebagai list data password, kemudian kita dapat mengklik button start attack.

 ![](Gambar/gambar24.png)

9. Setelah itu, akan tertampil sebuah modal yang menampilkan list password yang dicoba sebelumnya, dan memuat informasi status dan length dan data lain. Disini semua 401 (tidak memiliki autorisasi)  hasilnya kecuali data terakhir "admin123" yang memiliki status 200 (memiliki autorisasi)

 ![](Gambar/gambar25.png)

10. Kemudian saya mencoba untuk login menggunakan "admin123" disini saya berhasil untuk login sebagai admin dan dapat mengakses keranjang serta profile dari akun admin yang ada di dalam owasp juice shop.

![](Gambar/gambar26.png)

![](Gambar/gambar27.png)

![](Gambar/gambar28.png)

![](Gambar/gambar29.png)

![](Gambar/gambar30.png)

## Kesimpulan

Disini saya berhasil membuktikan bahwa website owasp juice shop ini masih memiliki kerentanan yang mana disebutkan dalam owasp 10 yakni broken access control dimana saya dapat melihat keranjang dari user lain dan login sebagai admin padahal saya tidak terdaftar dan belum mengetahui password admin sebelumnya.


