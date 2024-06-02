> ## Intent
>> [Back](https://github.com/StudyClubUnida/AMOLED/blob/main/Android/Modul%20Android.md)

- **_Intent_** adalah mekanisme yang digunakan untuk menjalankan aksi dan memfasilitasi komunikasi antar komponen aplikasi seperti _Activity_, _Service_, dan _Broadcast Receiver_.

    #### Intent memiliki dua jenis:

    - **_Explicit Intent_:** Digunakan untuk menjalankan komponen lain di dalam aplikasi yang sama dengan tujuan yang jelas. Misalnya, berpindah dari satu Activity ke Activity lain dalam aplikasi yang sama.

    <h1 align="center">
        <img src="https://github.com/Study-Club-Unida/AMOLED/blob/main/Android/Assets/intent.png" width="400"></img>
    </h1>

    - **_Implicit Intent_:** Digunakan untuk menjalankan aksi tertentu tanpa menentukan aplikasi tujuan secara spesifik. Sistem akan mencari aplikasi yang mampu menangani aksi tersebut dan memberikan pilihan kepada pengguna jika ada lebih dari satu aplikasi yang sesuai. Contohnya, membuka peta (bisa menggunakan Google Maps atau Waze) atau mengambil foto (bisa menggunakan aplikasi kamera bawaan atau aplikasi kamera pihak ketiga).

    <h1 align="center">
        <img src="https://github.com/StudyClubUnida/AMOLED/blob/main/Android/Assets/implicit_explicit_intents_android.jpg" width="400"></img>
    </h1>

- Fungsi `putExtra(key, value)` digunakan untuk menambahkan data ke dalam Intent dalam format pasangan kunci-nilai.
- Fungsi `intent.getFooExtra(key)` digunakan untuk mengambil data dari Intent berdasarkan kunci yang diberikan. "Foo" menunjukkan tipe data dari nilai yang dikirim.
- Parcelable adalah antarmuka yang memungkinkan pengiriman objek melalui Intent.
- Parcelize adalah plugin yang dapat menghasilkan kode implementasi Parcelable secara otomatis.
- Fungsi `setResult` digunakan untuk mengirimkan hasil kembali ke Activity yang memanggilnya.
- Fungsi `registerForActivityResult` digunakan untuk menerima data yang dikirim oleh `setResult` dari Activity lain. Fungsi ini menghasilkan objek `ActivityResultLauncher` yang digunakan untuk memulai Activity lain.
- Fungsi `finish()` digunakan untuk menutup atau mengakhiri Activity dan kembali ke Activity sebelumnya.
- Debugging adalah proses mengidentifikasi dan memperbaiki kesalahan atau masalah dalam kode program.
- Logging adalah cara untuk menampilkan informasi di Logcat, berguna untuk memeriksa nilai objek atau memverifikasi fungsi.
- Debug breakpoint adalah fitur di Android Studio yang memungkinkan Anda menghentikan eksekusi kode pada baris tertentu untuk memeriksa nilai variabel saat aplikasi berjalan.
- Error `NullPointerException` terjadi ketika mencoba mengakses variabel yang memiliki nilai null.
