> ## Local Data
>> [Back](https://github.com/StudyClubUnida/AMOLED/blob/main/Android/Modul%20Android.md)

- _**App Storage**_ adalah tempat penyimpanan yang dikhususkan untuk setiap aplikasi, sedangkan Shared Storage merupakan tempat penyimpanan bersama yang bisa diakses oleh aplikasi lain.
- Jika ingin mengakses App Storage, gunakan `getFilesDir()/getCacheDir()` untuk internal storage dan `getExternalFilesDir()/getExternalCacheDir()` untuk external storage.
- **_MediaStore_** merupakan mekanisme untuk mengakses berkas berupa media, seperti image, video, audio, dan file download. Untuk memakainya, gunakan contentResolver.
- **_Storage Access Framework_** merupakan picker bawaan sistem untuk mengakses berbagai macam file, seperti dokumen dan pdf.
- **_SharedPreference_** merupakan penyimpanan data yang menggunakan format key-value.
- **_DataStore_** merupakan penyimpanan data terbaru dengan format key-value yang lebih aman karena dapat berjalan secara asynchronous menggunakan Flow.
  #### DataStore hadir dalam dua bentuk:
  - **Preference DataStore:** Mirip dengan SharedPreferences, ini adalah cara sederhana untuk menyimpan data dalam format XML.
  - **Proto DataStore:** Menggunakan skema protocol buffer yang lebih canggih, penyimpanan ini menawarkan keamanan tipe data yang lebih kuat.


- **_SQL_** (_Structured Query Language_), adalah bahasa standar yang digunakan untuk berkomunikasi dengan database, memungkinkan pengguna untuk mengambil, menambah, mengubah, atau menghapus data.
- **_SQLite_** adalah jenis database yang ringkas dan efisien yang ideal untuk perangkat dengan sumber daya terbatas seperti smartphone. Tidak seperti perangkat lunak database besar, _SQLite_ tidak memerlukan proses login yang rumit atau pengaturan administratif yang ekstensif.
    
    #### Beberapa keuntungan menggunakan local database:
  - **Pengalaman pengguna yang lebih baik:** Data ditampilkan lebih cepat dan responsif.
  - **Hemat daya baterai:** Tidak perlu terus-menerus mengakses jaringan.
  - **Menghemat kuota internet:** Data diambil dari penyimpanan lokal, bukan dari server.
  - **Mengurangi beban server dan bandwidth:** Mengurangi lalu lintas jaringan yang tidak perlu.
  - **Aplikasi tetap berfungsi tanpa internet:** Data tetap dapat diakses dan aplikasi tetap dapat digunakan secara offline.

- **_Room_** adalah _library_ Jetpack yang menyederhanakan pengelolaan database SQLite lokal, menjadikannya lebih cepat dan mudah. Sebagai _library_ ORM (_Object Relational Mapping_), Room memungkinkan Anda memetakan tabel database secara langsung ke dalam kelas data dalam aplikasi Anda.

  #### Room memiliki tiga komponen kunci:
  - **_Database_**: Berperan sebagai pintu gerbang utama untuk menghubungkan aplikasi Anda dengan database.
  - **_Entity_**: Mewakili struktur tabel yang terdapat dalam database, mendefinisikan bagaimana data diatur.
  - **_DAO (Data Access Object)_**: Menyediakan metode-metode untuk berinteraksi dengan database, seperti operasi CRUD (Create, Read, Update, Delete).


- **_Singleton_** adalah pola desain yang memastikan hanya ada satu instance dari suatu objek dan menyediakan cara tunggal untuk mengaksesnya.
- **_Repository_** adalah kelas yang bertanggung jawab untuk mengelola semua operasi terkait data, baik itu berasal dari layanan web atau database lokal.
- Class B dikatakan sebagai Dependency dari class A jika class A menggunakan fungsi atau fitur yang ada di dalam class B.
- **_Dependency Injection (DI)_** adalah teknik di mana dependensi suatu kelas dipindahkan keluar dari kelas tersebut dan kemudian "disuntikkan" ke dalamnya dari luar.
  
  #### Berikut manfaat menerapakan Dependency Injection (DI):
  - Tidak saling terikat (loosely coupled) sehingga dependency mudah diubah-ubah.
  - Depedency bisa juga digunakan di tempat lain.
  - Kode menjadi lebih mudah dites.

Perbedaan dari masing-masing penyimpanan data, lihatlah tabel berikut:

| Jenis Penyimpanan      | Tipe Data Penyimpanan | Lama Penyimpanan                               |
|:-----------------------| :-------------------- | :----------------------------------------------- |
| onSaveInstanceState    | Key-value             | Hanya ketika aplikasi dibuka                    |
| DataStore              | Key-value             | Sampai aplikasi di-uninstall/clear data          |
| SQLite Database        | Tabel data lokal       | Sampai aplikasi di-uninstall/clear data.         |
| Room Database          | Tabel data lokal (ORM) | Sampai aplikasi di-uninstall/clear data.         |
| App-Specific Storage   | Penyimpanan media privat | Sampai aplikasi di-uninstall/clear data.         |
| Shared Storage         | Penyimpanan media publik  | Tetap ada walaupun di-uninstall/clear data.      |
| Network/Server         | Tabel data            | Selama server aktif                              |


### [Praktikum](#praktikum)
