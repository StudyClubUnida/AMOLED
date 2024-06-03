> ## Recycler View
>> [Back](https://github.com/StudyClubUnida/AMOLED/blob/main/Android/Modul%20Android.md)


- **_RecyclerView_** adalah komponen yang digunakan untuk menampilkan data dalam jumlah besar secara efisien.
- **_RecyclerView_** hanya membuat objek sebanyak yang terlihat di layar ditambah beberapa objek di atas dan di bawahnya. Saat objek keluar dari layar, **_RecyclerView_** mendaur ulang tampilan objek tersebut untuk digunakan kembali, sehingga penggunaan memori menjadi lebih efisien.
- Untuk menampilkan data menggunakan RecyclerView, Anda perlu memahami beberapa komponen penting:
    - **RecyclerView:** Merupakan komponen ViewGroup yang harus ditambahkan ke dalam file XML layout Anda. Komponen ini berfungsi sebagai wadah untuk menampilkan data.
    - **LayoutManager:** Bertugas mengatur tata letak item-item di dalam RecyclerView. Terdapat beberapa pilihan LayoutManager yang dapat Anda gunakan:

    <h1 align="center">
        <img src="https://github.com/Study-Club-Unida/AMOLED/blob/main/Android/Assets/recycler-view.jpeg" width="400"></img>
    </h1>

    > **_LinearLayoutManager_:** Menyusun item dalam satu kolom secara linear, baik vertikal maupun horizontal.

    > **_GridLayoutManager_:** Menyusun item dalam beberapa kolom membentuk grid.

    > **_StaggeredLayoutManager_:** Menyusun item dengan tinggi yang berbeda-beda, menciptakan tampilan yang lebih dinamis.

    - **_Data source_:** sumber data yang akan ditampilkan ke dalam RecyclerView, biasanya berupa List/ArrayList.

    - **_Layout item_:** berkas tampilan XML untuk setiap baris item.

    - **RecyclerView.Adapter:** Kelas yang berperan sebagai jembatan antara sumber data dengan RecyclerView. Adapter memiliki beberapa fungsi penting:
        - **`onCreateViewHolder()`:** Membuat ViewHolder baru yang terhubung dengan layout item, menentukan tampilan setiap item dalam RecyclerView.
        - **`onBindViewHolder()`:** Mengisi data dari sumber data ke dalam ViewHolder sesuai dengan posisi item, memastikan setiap item menampilkan data yang benar.
        - **`getItemCount()`:** Menentukan jumlah total item yang akan ditampilkan dalam RecyclerView.

    - **RecyclerView.ViewHolder:** Berfungsi untuk mendaur ulang item dan menentukan cara data ditampilkan dalam layout item. ViewHolder menyimpan referensi ke tampilan setiap item, sehingga tidak perlu mencari tampilan tersebut setiap kali item diperbarui.

- Untuk mendapatkan `context` di dalam Adapter, gunakan `itemView.getContext()`.

- Terdapat beberapa cara untuk menambahkan aksi `onClick` pada item RecyclerView:
    1. **Langsung menambahkan `setOnClickListener` di dalam adapter:** Ini adalah cara paling sederhana, namun kurang fleksibel jika Anda ingin menangani klik di luar adapter.
    2. **Membuat callback menggunakan interface pada parameter:** Cara ini lebih terstruktur dan memungkinkan penanganan klik di luar adapter. Anda membuat interface dengan metode `onClick` dan meneruskannya ke adapter melalui konstruktor.
    3. **Menambahkan lambda pada parameter:** Mirip dengan cara sebelumnya, tetapi menggunakan lambda expression untuk membuat kode lebih ringkas.

    Pilihan metode tergantung pada preferensi dan kompleksitas penanganan klik yang dibutuhkan.

- Library adalah alat bantu atau kode sumber yang telah dibuat oleh pihak lain (pihak ketiga) yang dapat Anda gunakan dalam aplikasi Anda.
- Setelah menambahkan dependency pada file `build.gradle.kts` (module:app), klik `Sync Now` untuk mengunduh library tersebut.
- Untuk menampilkan gambar dari internet, Anda bisa menggunakan library **Glide**, **Picasso**, **Fresco**, dan **Coil**.

