> ## View Binding
>> [Back](https://github.com/StudyClubUnida/AMOLED/blob/main/Android/Modul%20Android.md)

**_View binding_** adalah fitur yang memudahkan Anda menulis kode yang berinteraksi dengan tampilan. Setelah diaktifkan dalam sebuah modul, view binding akan menghasilkan class binding untuk setiap file tata letak XML yang ada dalam modul tersebut. Instance class binding berisi referensi langsung ke semua tampilan yang memiliki ID di tata letak yang terkait. Pada umumnya, view binding menggantikan `findViewById`.

### 1. Persiapan Awal
**_View binding_** diaktifkan di level modul. Untuk mengaktifkan view binding dalam modul, tambahkan elemen **_viewBinding_** ke file `build.gradle` nya, seperti yang ditunjukkan pada contoh berikut:

```
android {
        ...
        viewBinding {
            enabled = true
        }
    }
```

### 2. Penggunaan viewBinding
Jika view binding diaktifkan untuk sebuah modul, sebuah class binding akan dihasilkan untuk setiap file tata letak XML yang berada di dalam modul. Setiap class binding berisi referensi ke tampilan **_root_** dan semua tampilan yang memiliki ID. Nama class binding dihasilkan dengan mengonversi nama file XML menjadi camel case dan menambahkan kata `Binding` ke bagian akhirnya.

Misalnya, pada file tata letak dengan nama `main_activity.xml`:

```
<LinearLayout ... >
        <TextView android:id="@+id/name" />
        <ImageView android:cropToPadding="true" />
        <Button android:id="@+id/button"
            android:background="@drawable/rounded_button" />
</LinearLayout>
```

### 3. Implementasi viewBinding pada Activity
Untuk menyiapkan instance class binding agar dapat digunakan dengan suatu aktivitas, lakukan langkah-langkah berikut dalam metode `onCreate()` activity:

```
   private lateinit var binding: ActivityMainBinding

    override fun onCreate(savedInstanceState: Bundle) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater) 
        setContentView(binding.root)
    }
```

Sekarang, Anda dapat menggunakan instance class binding untuk merujuk ke tampilan mana pun:

```
binding.name.text = viewModel.name
binding.button.setOnClickListener { viewModel.userClicked() }
```

### 4. Implementasi viewBinding pada Fragment
Untuk menyiapkan instance class binding agar dapat digunakan dengan fragmen, lakukan langkah-langkah berikut dalam metode `onCreateView()` fragment:

```
private var _binding: ResultProfileBinding? = null
// This property is only valid between onCreateView and
// onDestroyView.
private val binding get() = _binding!!

override fun onCreateView(
    inflater: LayoutInflater,
    container: ViewGroup?,
    savedInstanceState: Bundle?
): View? {
    _binding = ResultProfileBinding.inflate(inflater, container, false)
    val view = binding.root
    return view
}

override fun onDestroyView() {
     super.onDestroyView()
     _binding = null
}
```

### 5. Perbedaan viewBinding dengan findViewById
**_View binding_** memiliki keunggulan penting dibandingkan `findViewById`:

- **_Keamanan null_**

  View binding menciptakan referensi langsung ke tampilan, tidak ada risiko pengecualian pointer null akibat ID tampilan yang tidak valid. Selain itu, jika tampilan hanya ada dalam beberapa konfigurasi tata letak, kolom yang berisi referensinya dalam class binding itu akan ditandai sebagai `@Nullable`.
 
- **_Keamanan jenis_**

  Kolom di setiap class binding memiliki jenis yang cocok dengan tampilan yang direferensikannya dalam file XML. Dengan begitu, tidak ada risiko pengecualian cast class.

Perbedaan ini berarti inkompatibilitas antara tata letak dan kode Anda akan menyebabkan build gagal pada waktu kompilasi, bukan pada waktu proses.

