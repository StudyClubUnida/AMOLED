> ## Networking
>> [Back](https://github.com/StudyClubUnida/AMOLED/blob/main/Android/Modul%20Android.md)


- **_Thread_** adalah unit terkecil dalam pemrosesan CPU, bertugas menjalankan satu tugas pada satu waktu.
- Secara default, semua komponen aplikasi Android berjalan pada _main thread_ (_UI thread_).
- Tugas berat yang memakan waktu lebih dari beberapa milidetik harus dipindahkan ke _background thread_, contohnya seperti pemrosesan gambar, akses database, model machine learning, atau pengambilan data dari jaringan.
- Jika tugas berat dijalankan di main thread, aplikasi akan mengalami macet, lambat, bahkan bisa tertutup paksa karena ANR (_Application Not Responding_).

    #### Ada dua mekanisme dalam menjalankan tugas dalam suatu sistem.
    - **_Asynchronous_**: proses berjalan secara paralel alias tidak berurutan sehingga proses lain bisa masuk dan layar Android masih bisa kita jalankan.
    - **_Synchronous_**: proses berjalan secara berurutan sehingga kita harus menunggu proses tersebut selesai terlebih dahulu sebelum melakukan proses lainnya.

<h1 align="center">
  <img src="https://www.koyeb.com/static/images/blog/sync-vs-async-schema.png" width="400"></img>
</h1>

- Hindari mengakses komponen UI langsung dari _background thread_. Pastikan untuk memindahkan operasi pembaruan UI ke _main thread_ terlebih dahulu.
- **_Executor_** adalah komponen di Android yang memungkinkan pengelolaan beberapa thread sekaligus, termasuk mengatur urutan eksekusi, penjadwalan, dan menjalankan proses secara paralel.

**_Coroutine_** adalah fitur Kotlin untuk menangani tugas konkuren (concurrency) dengan lebih baik. Keunggulannya antara lain:

- **Ringan dan Efisien:** Jutaan coroutine dapat berjalan pada beberapa thread, berbeda dengan thread yang lebih berat.
- **Kode Lebih Sederhana:** Coroutine menghilangkan kebutuhan akan callback, membuat kode lebih ringkas dan mudah dibaca.
- **Mengurangi Kebocoran Memori:** Coroutine dijalankan dalam Scope yang membentuk structured concurrency, memudahkan pengelolaan dan mengurangi risiko kebocoran memori.

- Banyak library Jetpack, seperti _Retrofit_, _WorkManager_, dan _Room_, sudah terintegrasi dengan _Coroutine_, menjadikannya pilihan yang lebih menarik untuk penanganan tugas konkuren di Android.

    #### Terdapat dua cara untuk menjalankan coroutine:
    1. **Launch:** Digunakan ketika kita hanya ingin memulai proses tanpa memerlukan hasil kembaliannya (_fire and forget_).
    2. **Async:** Digunakan ketika kita perlu menunggu hasil dari proses yang dijalankan. Hasilnya akan dikembalikan dalam bentuk Deferred, yang kemudian bisa kita ambil nilainya menggunakan fungsi `await`.

- **_Dispatcher_** berfungsi untuk menentukan di mana Coroutine akan dijalankan. Berikut beberapa pilihan **_Dispatcher_** yang dapat digunakan:

    - **Dispatchers.Default:** Pilihan default jika tidak ada Dispatcher yang ditentukan secara khusus. Cocok untuk tugas yang membutuhkan penggunaan CPU yang intensif, seperti memproses data dalam jumlah besar.
    - **Dispatchers.IO:** Digunakan untuk menjalankan fungsi yang melibatkan operasi baca-tulis data ke jaringan atau penyimpanan, seperti membaca atau menulis data ke database dan server.
    - **Dispatchers.Main:** Digunakan untuk menjalankan fungsi di _Main Thread_, terutama untuk memperbarui tampilan UI (_User Interface_).

- **_Suspend Function_** digunakan untuk memanggil kode Coroutine. **_Suspend Function_** harus dipanggil oleh **_Suspend Function_** lain atau menggunakan **_Coroutine Scope_**.

- _**Scope**_ berfungsi untuk mengatur masa hidup dan mengelola Coroutine. Beberapa jenis Scope yang sering digunakan di Android antara lain:
    - **CoroutineScope:** Scope umum untuk memantau coroutine yang sedang berjalan. Coroutine di dalamnya dapat dibatalkan kapan saja dengan memanggil fungsi `cancel()`.
    - **LifecycleScope:** Scope khusus yang terikat dengan siklus hidup Activity atau Fragment. Coroutine dalam scope ini akan otomatis dibatalkan saat siklus hidup komponen mencapai tahap `onDestroy`.
    - **ViewModelScope:** Scope yang digunakan khusus di ViewModel. Coroutine dalam scope ini akan otomatis dibatalkan ketika ViewModel dibersihkan (`onCleared`).

- **_Web API_** (_Application Programming Interface_) adalah layanan yang memungkinkan dua aplikasi yang berbeda untuk berkomunikasi dan bertukar data melalui jaringan. Dengan Web API, kita bisa dengan mudah mengambil atau mengirim data ke layanan tersebut.

- **_HTTP_** adalah protokol yang digunakan untuk pertukaran data antara server dan client. Dalam protokol ini, terdapat beberapa metode permintaan (_request method_) yang umum digunakan untuk operasi CRUD (_Create, Read, Update, Delete_), antara lain:
    * **POST:** Digunakan untuk membuat data baru.
    * **GET:** Digunakan untuk membaca atau mengambil data.
    * **PUT:** Digunakan untuk mengubah atau memperbarui data yang sudah ada.
    * **DELETE:** Digunakan untuk menghapus data.

- Berikut adalah contoh URL yang merupakan API beserta penjelasan parameter-parameternya:
**[https://reqres.in/api/users?page=1&per_page=10](https://reqres.in/api/users?page=1&per_page=10)**

    - **Path:** "users" menunjukkan bagian dari API yang akan diakses.
    - **Query 1:** "page" dengan nilai "1" menunjukkan halaman data yang ingin ditampilkan.
    - **Query 2:** "per_page" dengan nilai "10" menunjukkan jumlah data per halaman yang ingin ditampilkan.
    - **"?"** digunakan sebagai pemisah antara path dan parameter pertama.
    - **"&"** digunakan sebagai pemisah antara parameter-parameter selanjutnya.
    - **"="** digunakan untuk memberikan nilai pada masing-masing parameter.

- **_JSON (Javascript Object Notation)_** adalah format yang ringan dan mudah dibaca untuk bertukar dan menyimpan data, kompatibel dengan hampir semua bahasa pemrograman.
- **_JSONArray_** ditandai dengan tanda kurung siku [ ], berisi kumpulan **_JSONObject_** yang dipisahkan koma. **_JSONObject_** sendiri ditandai dengan kurung kurawal { }.
- Proses jaringan (networking) harus dilakukan secara asinkron untuk menghindari eror **_networkOnMainThreadException_**.
- Saat mengirim permintaan ke server, Anda akan menerima kode status. Kode 200 berarti koneksi berhasil, sedangkan kode 4xx (seperti 401, 403, 404, dll.) menunjukkan koneksi gagal.
- **_Retrofit_**, sebuah library populer dari Square, memudahkan proses networking ke Web API. Dengan bantuan **_GSON Converter_**, proses parsing data JSON menjadi objek Java dapat dilakukan secara otomatis.

- Berikut adalah penjelasan singkat mengenai berbagai anotasi (annotation) yang digunakan dalam Retrofit:

    - **@Headers:** Menambahkan informasi tambahan pada header permintaan, seperti otorisasi, jenis data, dan sebagainya.
    - **@Query:** Menambahkan parameter pada metode @GET.
    - **@Path:** Mengganti bagian variabel pada endpoint dengan nilai yang ditentukan. Contohnya, `{id}` akan digantikan dengan nilai `id`.
    - **@FormUrlEncoded:** Menandai fungsi pada @POST sebagai form-url-encoded.
    - **@Field:** Menambahkan parameter pada metode @POST.
    - **@Multipart:** Menandai fungsi sebagai multipart, yang memungkinkan pengiriman data dalam beberapa bagian.
    - **@Part:** Mengirimkan file menggunakan multipart.
    - **@PartMap:** Mengirimkan data selain file dalam multipart.

- **_Logging Interceptor_** merupakan library tambahan yang digunakan untuk menampilkan hasil response pada Logcat.

- **_OkHttpClient_** merupakan library tambahan yang digunakan untuk menangani koneksi jaringan, seperti menangani koneksi berkarakter, mengirimkan permintaan, dan menerima respon.