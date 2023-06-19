> ## Android Architecture
>> [Back](https://github.com/StudyClubUnida/AMOLED/blob/main/Android/Modul%20Android.md)

### a. Modern Android Development
Seperti yang Anda tahu, perkembangan Android sangatlah cepat. Apa yang bagus dilakukan 5 tahun lalu, belum tentu masih bagus dilakukan sekarang. Hal itu karena banyak fitur baru  yang hadir maupun karena ada update dari fitur yang sudah ada. Tentu pembaruan ini bertujuan untuk memberikan performa yang lebih baik pada aplikasi Anda.

Nah, supaya Anda tidak bingung apa saja hal yang baru tersebut dan mana yang direkomendasikan, Google telah menggaungkan konsep **_Modern Android Development_**. Ia merupakan blueprint untuk para developer supaya bisa lebih produktif dan menghasilkan aplikasi yang jauh lebih bagus nan kompatibel untuk jutaan device.

Kita akan bahas 4 pilar penting yang ada pada Modern Android Development.


Perlu diketahui bahwa saat ini komponen Jetpack terus bertambah hingga lebih dari 70 library dan dibagi menjadi 9 bagian yaitu:

<center>
  <img src="https://github.com/StudyClubUnida/AMOLED/blob/main/Android/Assets/Modern%20Android%20Development.png" width="400">
</center>
 
1. **_Language_**

    Dari sisi bahasa, Android telah merekomendasikan Kotlin sebagai bahasa utama setelah resmi menjadi bahasa alternatif. Hal ini tak luput dari kelebihan-kelebihan Kotlin yang membuat para developer senang, yakni seperti bahasanya yang ringkas, cepat, dan aman. Selain itu, karena sifatnya yang interoperability, banyak sekali developer yang bisa beralih dari bahasa Java ke Kotlin dengan cepat. Tak ayal, hampir 95% dari 1000 aplikasi teratas di Play Store menggunakan Kotlin.

2. **_Tools_**

   Dari sisi tools, Android Studio menjadi pilihan terbaik untuk mengembangkan aplikasi Android. Hal ini karena ia telah mengakomodasi semua kebutuhan dari awal sampai akhir. Mulai dari membuat project dengan template, mendesain dengan menggunakan Layout Editor, testing menggunakan emulator, sampai membuat file APK/AAB bisa dilakukan di Android Studio.

3. **_APIs_**

   Inilah bagian yang akan kita bahas lebih dalam pada kelas ini, yakni tentang API yang menggunakan komponen Android Jetpack. Jetpack memang dirancang untuk memecahkan masalah yang sering dihadapi oleh para Developer. Penasaran apa saja komponen yang ada di dalam Jetpack dan bagaimana ia bisa membantu Anda? Tenang, itu semua akan terjawab pada modul selanjutnya.

4. **_Distribution_**

    Mungkin saat ini Anda mengenal APK sebagai format pendistribusian aplikasi. Namun, ketahuilah bahwa format yang terbaik saat ini adalah AAB (Android App Bundle). Sebab ukuran aplikasi yang diunduh bisa menjadi jauh lebih kecil. Hal ini karena sifatnya yang dinamis, di mana ia dapat mengunduh hanya bagian (seperti bahasa, arsitektur, dan density) yang diperlukan saja.

### b. Pengenalan Android Jetpack

Pada Google I/O 2018, Google resmi memublikasikan Android Jetpack. Jetpack merupakan kumpulan dari komponen library, tools, dan panduan untuk membuat aplikasi yang bagus [9]. Ia dapat membantu proses pengembangan aplikasi android menjadi lebih mudah dan cepat sesuai dengan best practice.

<img src="https://github.com/StudyClubUnida/AMOLED/blob/main/Android/Assets/ic_androidjetpack_logo.png" width="300">

Jetpack terdiri dari beberapa paket library dengan awalan androidx yang terpisah dari API platform. Jetpack juga menawarkan kompatibilitas dengan versi sebelumnya dan lebih sering diperbarui dibandingkan platform Android. Alhasil, Anda selalu dapat mengakses versi komponen Jetpack yang terbaru dan terbaik tanpa memikirkan kompatibilitas.

### Keuntungan Menggunakan Jetpack
- **_Mengikuti Best Practices_**

  Dengan menerapkan best practices yang modern, komponen Android Jetpack memungkinkan kita untuk mengurangi tingkat crash yang bakal terjadi dan juga menghindari terjadinya memory leaks (kebocoran memori). Komponen Android Jetpack juga memiliki dukungan kompatibilitas pada versi lama sehingga tidak perlu khawatir dengan masalah versi.
- **_Mengurangi Kode Boilerplate_** 

    Android Jetpack mampu mengelola kode yang berulang-ulang seperti background task, navigation, dan manajemen lifecycle, sehingga Anda bisa lebih fokus pada fitur untuk menjadikan aplikasi Anda menarik.
- **_Mengatasi Fragmentation_**

    Yang dimaksud dengan fragmentation di sini adalah kode yang berbeda untuk versi Android yang berbeda, sehingga Anda harus menambahkan logika percabangan untuk versi yang berbeda tersebut. Dengan komponen Jetpack, Anda dapat mengurangi hal tersebut karena ia sudah support untuk semua versi dan menghasilkan output yang konsisten pada versi dan device yang berbeda.

### c. Komponen Android Jetpack
Jika dilihat, sebenarnya beberapa komponen ini sudah ada sebelum Jetpack dipublikasikan, seperti AppCompat, Fragment, dan Notifications. Jadi, sebenarnya Jetpack bukanlah hal yang sepenuhnya baru. Namun, supaya terkumpul menjadi satu, dibuatlah Android Jetpack supaya lebih mudah untuk kita pelajari.

Perlu diketahui bahwa saat ini komponen Jetpack terus bertambah hingga lebih dari 70 library dan dibagi menjadi 9 bagian yaitu:

1. **_Beyond Phone_**

   Berisi berbagai macam library yang digunakan untuk membuat aplikasi Android pada device selain telepon biasa:

| Library                                                                                                     | Deskripsi                                                                           |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| <a href="https://developer.android.com/jetpack/androidx/releases/car-app" target="_blank">car-app</a>       | Membuat aplikasi Android untuk mobil.                                               |
| <a href="https://developer.android.com/jetpack/androidx/releases/tvprovider" target="_blank">tvprovider</a> | Membuat aplikasi Android untuk TV.                                                  |
| <a href="https://developer.android.com/jetpack/androidx/releases/wear" target="_blank">wear</a>             | Membuat aplikasi Android untuk Wear OS.                                             |
| <a href="https://developer.android.com/jetpack/androidx/releases/window" target="_blank">window</a>         | Mendukung aplikasi supaya mendukung berbagai macam device, seperti foldable device. |

2. **_Data_**

   Berisi berbagai macam library yang digunakan untuk mengolah data:

| Library                                                                                                     | Deskripsi                                                                                            |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| <a href="https://developer.android.com/jetpack/androidx/releases/datastore" target="_blank">datastore</a>   | Menyimpan data secara asynchronous dan konsisten yang mengatasi beberapa kelemahan SharedPreference. |
| <a href="https://developer.android.com/jetpack/androidx/releases/preference" target="_blank">preference</a> | Membuat halaman setting yang sudah terintegrasi dengan SharedPreference.                             |
| <a href="https://developer.android.com/jetpack/androidx/releases/room" target="_blank">room *</a>           | Abstraksi dari SQLite untuk mengelola database di lokal.                                             |
| <a href="https://developer.android.com/jetpack/androidx/releases/sqlite" target="_blank">sqlite</a>         | Menyimpan dan mengelola database di lokal.                                                           |
| <a href="https://developer.android.com/jetpack/androidx/releases/work" target="_blank">work *</a>           | Menjadwalkan dan menjalankan deferred background task dengan basis constraint.                       |

3. **_Graphics_**

   Berisi berbagai macam library yang digunakan untuk mengatur gambar visual:

| Library                                                                                                                 | Deskripsi                                                                         |
|-------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| <a href="https://developer.android.com/jetpack/androidx/releases/dynamicanimation" target="_blank">dynamicanimation</a> | Membuat animasi yang halus dengan basis physics (seperti gravitasi dan tumbukan). |
| <a href="https://developer.android.com/jetpack/androidx/releases/interpolar" target="_blank">interpolator</a>           | Mengatur kecepatan animasi secara dinamis (seperti semakin cepat/lambat).         |
| <a href="https://developer.android.com/jetpack/androidx/releases/pallete" target="_blank">palette</a>                   | Mengambil palette warna dari suatu gambar.                                        |
| <a href="https://developer.android.com/jetpack/androidx/releases/transition" target="_blank">transition</a>             | Membuat animasi perubahan layout dengan menentukan bentuk awal dan akhir.         |
| <a href="https://developer.android.com/jetpack/androidx/releases/vectordrawable" target="_blank">vectordrawable</a>     | Membuat gambar vector dengan menggunakan XML.                                     |

4. **_Lifecycle_**

   Berisi berbagai macam library yang digunakan untuk mengatur lifecycle:

| Library                                                                                                     | Deskripsi                                                                 |
|-------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|
| <a href="https://developer.android.com/jetpack/androidx/releases/lifecycle" target="_blank">lifecycle *</a> | Membuat komponen yang dapat merespons terhadap perubahan lifecycle.       |
| <a href="https://developer.android.com/jetpack/androidx/releases/loader" target="_blank">loader</a>         | Menampilkan data yang dapat bertahan ketika terjadi configuration change. |

5. **_Media_**

   Berisi berbagai macam library yang berhubungan dengan media:

| Library                                                                                                           | Deskripsi                                                                     |
|-------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| <a href="https://developer.android.com/jetpack/androidx/releases/camera" target="_blank">camera *</a>             | Membuat aplikasi dapat menampilkan kamera.                                    |
| <a href="https://developer.android.com/jetpack/androidx/releases/exifinterface" target="_blank">exifinterface</a> | Menulis dan membaca informasi EXIF pada gambar.                               |
| <a href="https://developer.android.com/jetpack/androidx/releases/heifwriter" target="_blank">heifwriter</a>       | Membuat dan membaca format HEIF (High Efficiency Image File).                 |
| <a href="https://developer.android.com/jetpack/androidx/releases/media2" target="_blank">media2</a>               | Menampilkan dan mengatur media yang ada di Android.                           |
| <a href="https://developer.android.com/jetpack/androidx/releases/mediarouter" target="_blank">mediarouter</a>     | Mengaktifkan tampilan dan pemutaran media pada perangkat penerima jarak jauh. |

6. **_Navigation_**

   Berisi berbagai macam library yang digunakan untuk berpindah antar Activity/Fragment:

| Library                                                                                                         | Deskripsi                                                             |
|-----------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------|
| <a href="https://developer.android.com/jetpack/androidx/releases/drawerlayout" target="_blank">Drawerlayout</a> | Untuk menampilkan Navigation Drawer (menu samping yang bisa digeser). |
| <a href="https://developer.android.com/jetpack/androidx/releases/navigation" target="_blank">Navigation *</a>   | Menampilkan dan mengatur navigasi antar halaman dengan mudah.         |

7. **_Security_**

   Berisi berbagai macam library yang berfungsi untuk keamanan:

| Library                                                                                                   | Deskripsi                                                        |
|-----------------------------------------------------------------------------------------------------------|------------------------------------------------------------------|
| <a href="https://developer.android.com/jetpack/androidx/releases/biometric" target="_blank">biometric</a> | Melakukan autentikasi dengan menggunakan biometrik (sidik jari). |
| <a href="https://developer.android.com/jetpack/androidx/releases/security" target="_blank">security</a>   | Melakukan enkripsi pada preference dengan aman.                  |

8. **_Perfomance/Test_**

   Berisi berbagai macam library yang digunakan untuk membuat melihat performa atau melakukan testing:

| Library                                                                                                   | Deskripsi                                                        |
|-----------------------------------------------------------------------------------------------------------|------------------------------------------------------------------|
| <a href="https://developer.android.com/jetpack/androidx/releases/benchmark" target="_blank">benchmark</a> | Mengukur performa kode Anda secara akurat dalam Android Studio.  |
| <a href="https://developer.android.com/jetpack/androidx/releases/startup" target="_blank">startup</a>     | Menginisialisasi komponen secara otomatis saat aplikasi dimulai. |
| <a href="https://developer.android.com/jetpack/androidx/releases/test" target="_blank">test *</a>         | Melakukan pengujian.                                             |
| <a href="https://developer.android.com/jetpack/androidx/releases/tracing" target="_blank">tracing</a>     | Merekam aktivitas perangkat ke system trace buffer.              |

9. **_UI_**

   Berisi berbagai macam library yang berhubungan dengan UI:

| Library                                                                                                                     | Deskripsi                                                                                         |
|-----------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| <a href="https://developer.android.com/jetpack/androidx/releases/appcompat" target="_blank">appcompat *</a>                 | Mengizinkan API baru untuk dapat berjalan di Android versi lama.                                  |
| <a href="https://developer.android.com/jetpack/androidx/releases/cardview" target="_blank">cardview</a>                     | Membuat tampilan card.                                                                            |
| <a href="https://developer.android.com/jetpack/androidx/releases/compose" target="_blank">compose *</a>                     | Membuat UI programmatically dengan memanfaatkan composable function.                              |
| <a href="https://developer.android.com/jetpack/androidx/releases/constraintlayout" target="_blank">constraintlayout</a>     | Memposisikan dan mengatur ukuran widget lebih fleksibel dengan memanfaatkan relative positioning. |
| <a href="https://developer.android.com/jetpack/androidx/releases/coordinatorlayout" target="_blank">coordinatorlayout</a>   | Mengatur posisi top-level widget, seperti AppBarLayout dan FloatingActionButton.                  |
| <a href="https://developer.android.com/jetpack/androidx/releases/customview" target="_blank">customview</a>                 | Membuat tampilan view widget sendiri secara custom.                                               |
| <a href="https://developer.android.com/jetpack/androidx/releases/databinding" target="_blank">databinding *</a>             | Memasukkan data langsung ke komponen UI secara deklaratif.                                        |
| <a href="https://developer.android.com/jetpack/androidx/releases/emoji" target="_blank">emoji</a>                           | Menampilkan emoji yang mendukung semua versi Android.                                             |
| <a href="https://developer.android.com/jetpack/androidx/releases/fragment" target="_blank">fragment *</a>                   | Membuat tampilan yang fleksibel dan modular.                                                      |
| <a href="https://developer.android.com/jetpack/androidx/releases/gridlayout" target="_blank">gridlayout</a>                 | Membuat tampilan grid.                                                                            |
| <a href="https://m2.material.io/develop/android/" target="_blank">Material Design Components</a>                            | Komponen UI yang menerapkan prinsip Material Design.                                              |
| <a href="https://developer.android.com/jetpack/androidx/releases/paging" target="_blank">paging *</a>                       | Menampilkan data per halaman pada RecyclerView.                                                   |
| <a href="https://developer.android.com/jetpack/androidx/releases/recyclerview" target="_blank">recyclerview</a>             | Menampilkan banyak list data dengan memori yang sedikit.                                          |
| <a href="https://developer.android.com/jetpack/androidx/releases/slice" target="_blank">slice</a>                           | Menampilkan elemen UI di luar aplikasi.                                                           |
| <a href="https://developer.android.com/jetpack/androidx/releases/slidingpanelayout" target="_blank">slidingpanelayout</a>   | Menampilkan sliding pane.                                                                         |
| <a href="https://developer.android.com/jetpack/androidx/releases/swiperefreshlayout" target="_blank">swiperefreshlayout</a> | Mengimplementasikan konsep swipe-to-refresh.                                                      |
| <a href="https://developer.android.com/jetpack/androidx/releases/viewpager2" target="_blank">viewpager2</a>                 | Menampilkan halaman yang dapat digeser (swipe).                                                   |
| <a href="https://developer.android.com/jetpack/androidx/releases/webkit" target="_blank">webkit</a>                         | WebView dengan fitur terbaru yang bisa digunakan pada Android versi lama.                         |

Kita hanya akan fokus dengan komponen-komponen yang populer dan sering digunakan pada Android Architecture Component, seperti **_LiveData_** & **_ViewModel_** yang termasuk pada kategori **_Lifecycle_**, dan juga **_Room_** untuk menyimpan database-nya.

### d. Android Architecture Component
**_Android Architecture Components_** adalah kumpulan library yang membantu Anda untuk merancang aplikasi yang kuat, dapat diuji, dan dapat dikelola dengan mudah. Berikut ini adalah gambaran dari Architecture Components:

<center>
  <img src="https://github.com/StudyClubUnida/AMOLED/blob/main/Android/Assets/architecture%20component.png" width="400">
</center>

Gambar di atas, merupakan gambaran besar tentang Architecture Components. Setiap komponen memiliki fungsinya sendiri. Jika dipecah menjadi beberapa komponen :

1. **_View_** : Bisa dikatakan sebagai UI controller atau Fragment dan Activity yang berfungsi untuk menampilkan data atau melakukan aksi di dalam UI.
2. **_ViewModel_** : Memberikan data ke UI. Bertindak sebagai pusat komunikasi antara Repository dan UI. Fungsi ViewModel mempertahankan data dari configuration changes.
3. **_LiveData_** : Kelas pemegang data yang dapat di-observe. Selalu memegang/menyimpan data versi terbaru. Memberitahu pengamatnya atau observers ketika data telah berubah. Komponen UI hanya mengamati atau meng-observe data yang relevan dan tidak akan berhenti atau terus melanjutkan observation.
4. **_Repository_** : Anda menggunakan Repository untuk mengelola banyak sumber data, seperti berasal dari network, local, atau cache.
5. **_Room_** : Sumber data yang berasal dari local database. Room adalah sebuah library yang menyediakan lapisan abstraksi atas SQLite untuk memungkinkan akses database yang lebih kuat dengan memanfaatkan kekuatan SQLite.
6. **_Rest Client_** : Sumber data yang berasal dari network, seperti Rest API, Firebase atau data client lainnya.

Jadi, flow di atas menceritakan bagaimana sebuah Activity melakukan request data kepada ViewModel yang selanjutnya akan tersampaikan ke Repository. Di dalam Repository, aplikasi bisa mengetahui data berasal dari local atau network. Setelah Repository berhasil mendapatkan data, maka data akan dikirim ke kelas ViewModel. Dan ketika terjadi perubahan data, UI secara otomatis akan mengalami perubahan sesuai dengan data yang baru.
