> ## Style & Theme
>> [Back](https://github.com/StudyClubUnida/AMOLED/blob/main/Android/Modul%20Android.md)

- **_Style_** adalah kumpulan properti yang menentukan tampilan komponen _View_ atau _ViewGroup_.
- Menggunakan style membantu mengumpulkan atribut yang sering digunakan di banyak komponen sehingga perubahan dapat dilakukan di satu tempat saja.
- Style didefinisikan dalam file themes.xml yang terletak di _res_ → _values_.
- Semua style harus berada dalam tag resources. Setiap style dibuat menggunakan tag `style` dan tag `item` untuk menentukan propertinya.
- Untuk menerapkan style pada XML, gunakan properti `style="@style/NamaStyle"`.
- **_Theme_** adalah jenis style khusus yang diterapkan pada Activity dan Application dalam file AndroidManifest.xml.
- Dark Theme dapat menghemat baterai ponsel dan membuat aplikasi lebih mudah dibaca dalam kondisi minim cahaya.
- **_Material Design_** adalah panduan desain dari Google untuk menciptakan antarmuka pengguna (UI) dan pengalaman pengguna (UX) yang baik di Android.
- Untuk membuat theme, gunakan tag `style` dengan parent berupa Theme, misalnya `Theme.Material3.DayNight`.
- Beberapa atribut yang dapat dikustomisasi di dalamnya yaitu:

<h1 align="center">
  <img src="https://github.com/Study-Club-Unida/AMOLED/blob/main/Android/Assets/Material3 Theme.png" width="500"></img>
</h1>

- `colorPrimary`: Warna utama aplikasi yang akan muncul pada Action Bar dan komponen Button.
- `colorOnPrimary`: Warna teks atau ikon yang berada di atas elemen dengan warna `colorPrimary`.
- `colorSecondary`: Warna sekunder utama yang akan muncul pada Action Bar dan komponen EditText.
- `colorOnSecondary`: Warna teks atau ikon yang berada di atas elemen dengan warna `colorSecondary`.

Semua variabel warna ini sebaiknya disimpan dalam file `colors.xml` untuk memudahkan pengaturan dan pengelolaan warna dalam aplikasi Anda.
