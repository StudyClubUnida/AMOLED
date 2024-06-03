> ## Fragment
>> [Back](https://github.com/StudyClubUnida/AMOLED/blob/main/Android/Modul%20Android.md)

<h1 align="center">
    <img src="https://github.com/Study-Club-Unida/AMOLED/blob/main/Android/Assets/fragment-layout.jpeg" width="400"></img>
</h1>

- **_Fragment_** adalah bagian dari antarmuka pengguna (UI) selain Activity. Perbedaannya, kelas Fragment mewarisi (extends) dari kelas Fragment dan tidak perlu didaftarkan di AndroidManifest.xml.
- Fragment bersifat modular, artinya satu Activity dapat memiliki lebih dari satu Fragment. Selain itu, satu Fragment dapat digunakan kembali di beberapa Activity (_reusable_).
- Fragment memiliki siklus hidup sendiri yang terikat dengan siklus hidup Activity tempat ia berada.
- FragmentManager adalah kelas yang bertanggung jawab untuk mengelola Fragment di dalam Activity, seperti menambahkan (`add()`), mengganti (`replace()`), dan menghapus (`remove()`) Fragment.
- `supportFragmentManager` digunakan untuk mendapatkan instance FragmentManager di dalam Activity, sedangkan `parentFragmentManager` digunakan untuk mendapatkan instance FragmentManager dari Activity induk di dalam Fragment.
- `addToBackStack()` digunakan untuk menyimpan transaksi Fragment terakhir ke dalam back stack, yaitu tumpukan Fragment yang memungkinkan pengguna kembali ke Fragment sebelumnya dengan menekan tombol kembali.
- Perbedaan kode Activity dan Fragment

    | Fitur          | Activity                 | Fragment                                   |
    | :------------- | :----------------------- | :---------------------------------------- |
    | Context        | `this`                   | `requireActivity()`/`getActivity()`       |
    | Fungsi utama   | `onCreate`               | `onViewCreated`                             |
    | Cara mengambil View | `findViewById`           | `view.findViewById`                         |

- Untuk mengirimkan data ke Fragment, gunakan arguments yang berisi Bundle.